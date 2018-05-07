---
title: Platform::metadata::RuntimeClassName | Microsoft Docs
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
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 297a5089af7db43d837934e864e0925cd7b34a3d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="platformmetadataruntimeclassname"></a>Platform::Metadata::RuntimeClassName
Při použití definice třídy, zajistí, že Soukromá třída vrátí platný název z funkce getruntimeclassname –...  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
[Platform::Metadata::RuntimeClassName] name  
```  
  
#### <a name="parameters"></a>Parametry  
 name  
  
 Název existující veřejné typ, který je zobrazen v prostředí Windows Runtime.  
  
### <a name="remarks"></a>Poznámky  
 Pomocí tohoto atributu na privátní ref třídy můžete určit název typu vlastní runtime nebo pokud název existující nesplňuje požadavky na. Zadejte jako název veřejné rozhraní, který implementuje třídu.  
  
### <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak pomocí atributu. V tomto příkladu je název typu modulu runtime HellowWorldImpl Test::Native::MyComponent::IHelloWorld  
  
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