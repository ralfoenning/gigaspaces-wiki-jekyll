---
layout: post
title:  Type Converter
categories: XAP97
parent: cpp-api-basics.html
weight: 100
---

{% summary page|65 %}How to implement unsupported data types by creating user-defined packaging code.{% endsummary %}

# Overview

This example demonstrates serialization of data types that do not have built-in support in GigaSpaces c++ API. It shows you how to add your own code to convert your data type to the supported type, and vice versa.

{% infosign %} Supported types are stated in the `gs.xml` file. For more details, refer to the [C++ Mapping File](./cpp-api-mapping-file.html#type -- Supported Types) section.
{% refer %}It is assumed that you have read the [Writing Existing CPP Class to Space](./writing-existing-cpp-class-to-space.html) example which serves as a starting point for this example.{% endrefer %}

The code for this example is located at `<GigaSpaces Root>\cpp\examples\PocoUserPackaging`. This path will be referred to as `<Example Root>` in this page.

{% exclamation %} This example can be built and run on **Windows OS** only. If you use **Visual Studio** open the solution `PocoUserPackaging.sln` located in `<GigaSpaces Root>\cpp\examples\PocoUserPackaging\`. It is recommended to set your solution configuration to `Release` and do a rebuild that will generate all related files.

In this example, we translate an object of type `std::map` (which is not supported by GigaSpaces c++ API) into two buffers of type `std::vector` (which is a supported type).
By implementing this conversion code, we are able to read and write the original object type to and from the space just like any other supported type. In other words, we "teach" the space how to deal with our object, and as a result, we don't need to worry about conversion in the future.

To write and implement your conversion code:

1. Add the attribute `\[custom-serialization="true"\]` to the `class` element in the `gs.xml` file:

{% highlight xml %}
<class name="UserMessage" custom-serialization="true" persist="false" replicate="false" fifo="false" >
{% endhighlight %}

1. Write the type conversion code (use `<Example Root>\UserMessageSerializerPackaging.cpp` as an example):

{% highlight java %}
#define DONT_INCLUDE_SERIALIZER_EXPORTS

#include "UserMessageSerializer.cpp"

void	UserMessageSerializer::PreSerialize(const IEntry* ptr,bool isTemplate)
{
	if(!isTemplate)
	{
		UserMessage* p = (UserMessage*)ptr;

		p->buffer1.clear();
		p->buffer2.clear();
		std::map<std::string,std::string>::iterator iter = p->userMap.begin();
		for( ;iter!=p->userMap.end();iter++)
		{
			p->buffer1.push_back(iter->first); // push the key
			p->buffer2.push_back(iter->second);// push the data
		}
	}
};
void	UserMessageSerializer::PostDeserialize(IEntry* pNewObject)
{
	UserMessage* p = (UserMessage*)pNewObject;

	p->userMap.clear();
	for(int i=0;i<p->buffer1.size();i++)
	{
		p->userMap[p->buffer1[i]] = p->buffer2[i];// extract the data into the map
	}
	p->buffer1.clear();
	p->buffer2.clear();

};
{% endhighlight %}

{% infosign %} These functions extend the functionality of the generated serializer (`UserMessageSerializer.cpp`). The first function `PreSerialize` converts the map field to two vectors before the serialization. The second function `PostDeserialize` converts the two vectors back to a map field after the desrealization.

1. Handle the c++ serializer code generation, build the shared library (DLL) from your extension code, and place the library in the appropriate directory.

    {% infosign %} As shown in the [previous example](./writing-existing-cpp-class-to-space.html), you can use a custom build with the supplied makefile (at `<Example Root>/makefileSerializer.mk`).

1. **Rebuild** and run your code.

The console will have the following output:


    Retrieved a space proxy
    Did snapshot for UserMessage class


    Wrote a UserMessage to space.
    Content of the UserMessage's map (the unsupported field):
    map[key1] = ALPHA
    map[key2] = BETA
    Wrote another UserMessage to space.
    Content of the UserMessage's map (the unsupported field):
    map[key1] = ALPHA
    map[key2] = BETA
    map[key3] = GAMMA
    Took a UserMessage from the space.
    Content of the UserMessage's map (the unsupported field):
    map[key1] = ALPHA
    map[key2] = BETA
    map[key3] = GAMMA
    Read a UserMessage from the space.
    Content of the UserMessage's map (the unsupported field):
    map[key1] = ALPHA
    map[key2] = BETA
    Press Enter to end this example...
