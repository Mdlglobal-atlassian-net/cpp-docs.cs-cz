---
title: Platform::metadata::RuntimeClassName | Dokumentace Microsoftu
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::Metadata::RuntimeClassName
helpviewer_keywords:
- RuntimeClassName
- Platform::Metadata::RuntimeClassName
ms.assetid: fdef8f85-ab94-4edd-ba50-ee0da9358ff6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 024d9d7dce234b07620a108b1f11c240bd842ac6
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43765481"
---
# <a name="platformmetadataruntimeclassname"></a>Platform::Metadata::RuntimeClassName
Při použití u definice třídy, zajistí, že privátní třídu vrátí platný název z getruntimeclassname – funkce...  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
[Platform::Metadata::RuntimeClassName] name  
```  
  
#### <a name="parameters"></a>Parametry  
 name  
  
 Název existující veřejný typ, který je viditelný v modulu Windows Runtime.  
  
### <a name="remarks"></a>Poznámky  
 Pomocí tohoto atributu na privátní referenční třídy zadejte název vlastního modulu runtime typu nebo pokud na název existující nesplňuje požadavky. Zadejte jako název veřejného rozhraní, která třída implementuje.  
  
### <a name="example"></a>Příklad  
 Následující příklad ukazuje způsob použití atributu. V tomto příkladu je název typu runtime HellowWorldImpl Test::Native::MyComponent::IHelloWorld  
  
```  
  
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
  
## <a name="see-also"></a>Viz také  
 [Platform::Metadata – obor názvů](../cppcx/platform-metadata-namespace.md)