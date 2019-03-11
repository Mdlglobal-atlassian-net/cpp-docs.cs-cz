---
title: Platform::Metadata::RuntimeClassName
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::Metadata::RuntimeClassName
helpviewer_keywords:
- RuntimeClassName
- Platform::Metadata::RuntimeClassName
ms.assetid: fdef8f85-ab94-4edd-ba50-ee0da9358ff6
ms.openlocfilehash: d3de753c3a8897058333e02ce4294a0780d5b818
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/11/2019
ms.locfileid: "57738553"
---
# <a name="platformmetadataruntimeclassname"></a>Platform::Metadata::RuntimeClassName

Při použití u definice třídy, zajistí, že privátní třídu vrátí platný název z getruntimeclassname – funkce...

## <a name="syntax"></a>Syntaxe

```cpp
[Platform::Metadata::RuntimeClassName] name
```

#### <a name="parameters"></a>Parametry

*Jméno*<br/>
Název existující veřejný typ, který je viditelný v modulu Windows Runtime.

### <a name="remarks"></a>Poznámky

Pomocí tohoto atributu na privátní referenční třídy zadejte název vlastního modulu runtime typu nebo pokud na název existující nesplňuje požadavky. Zadejte jako název veřejného rozhraní, která třída implementuje.

### <a name="example"></a>Příklad

Následující příklad ukazuje způsob použití atributu. V tomto příkladu je název typu runtime HellowWorldImpl Test::Native::MyComponent::IHelloWorld

```cpp
namespace Test
{
    namespace Native
    {
        namespace MyComponent
        {
            public interface class IHelloWorld
            {
                Platform::String^ SayHello();
            };

            private ref class HelloWorldImpl sealed :[Platform::Metadata::RuntimeClassName] IHelloWorld
            {
            public:
                HelloWorldImpl();
                virtual Platform::String^ SayHello();
            };

            Platform::String^ HelloWorldImpl::SayHello()
            {
                return L"Hello World!";
            }
        }
    }
}
```

## <a name="see-also"></a>Viz také:

[Platform::Metadata – obor názvů](../cppcx/platform-metadata-namespace.md)
