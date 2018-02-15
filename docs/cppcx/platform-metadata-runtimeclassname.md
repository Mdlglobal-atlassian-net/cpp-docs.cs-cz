---
title: Platform::metadata::RuntimeClassName | Microsoft Docs
ms.custom: 
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::Metadata::RuntimeClassName
helpviewer_keywords:
- RuntimeClassName
- Platform::Metadata::RuntimeClassName
ms.assetid: fdef8f85-ab94-4edd-ba50-ee0da9358ff6
caps.latest.revision: 
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9addee7708fe1d0838168dd54f395459f9b71990
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
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