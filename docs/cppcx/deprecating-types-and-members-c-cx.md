---
title: "Místo začne typy a členy (C + +/ CX) | Microsoft Docs"
ms.custom: 
ms.date: 12/30/2016
ms.prod: windows-client-threshold
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: b20b01c1-a439-4ff0-8cf3-d7280c492813
caps.latest.revision: 
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a1062a507d6281e003d9294de1c1cb39b7c01f9e
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="deprecating-types-and-members-ccx"></a>Místo začne typy a členy (C + +/ CX)
V jazyce C + +/ CX, vyřazení prostředí Windows Runtime typů a členů pro producenti a spotřebitelé pomocí [zastaralé](http://msdn.microsoft.com/en-us/8b02ad36-3b5f-4361-888b-e6a99040e57c) atribut podporovaný. Jestliže jste využívají rozhraní API, do které byl použit tento atribut, můžete získat kompilaci zprávu upozornění, která označuje, že rozhraní API je zastaralá a také doporučuje rozhraní API alternativní používat. Ve vlastní veřejné typy a metody můžete použít tento atribut a zadejte vlastní zprávu.  
  
> [!CAUTION]
>  [Zastaralé](http://msdn.microsoft.com/en-us/8b02ad36-3b5f-4361-888b-e6a99040e57c) atribut lze použít pouze s typy prostředí Windows Runtime. Standardní C++ třídy a členy [__declspec(deprecated)](http://msdn.microsoft.com/library/044swk7y.aspx).  
  
### <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak přestat používat vlastní veřejná rozhraní API – například v prostředí Windows Runtime součásti. Druhý parametr typu [Windows: Foundation:: Metadata::DeprecationType](http://msdn.microsoft.com/en-us/ee01e63d-37d0-4273-accc-fca174f88bfa) Určuje, zda je rozhraní API je zastaralé nebo odebrat. Aktuálně pouze DeprecationType::Deprecated je podporována hodnota. Třetí parametr do atribut určuje [Windows::Foundation::Metadata::Platform](http://msdn.microsoft.com/en-us/1eae292d-1ab7-4d97-a58c-b0beffd51ef5) pro kterou platí atribut.  
  
```  
  
namespace wfm = Windows::Foundation::Metadata;  
  
public ref class Bicycle sealed  
{  
  
public:  
    property double Speed;  
  
    [wfm::Deprecated("Use the Speed property to compute the angular speed of the wheel", wfm::DeprecationType::Deprecate, 0x0)]  
    double ComputeAngularVelocity();  
};  
```  
  
## <a name="supported-targets"></a>Podporované cíle  
 Následující tabulka uvádí konstrukce, na které může být použit atribut zastaralé:  
  
||  
|-|  
|Ovládací prvek jazyka XAML|  
|delegát|  
|event|  
|pole výčtu|  
|enum|  
|struct |  
|– metoda|  
|třída|  
|rozhraní|  
|property|  
|Struktura pole|  
|parametrizované – konstruktor|  
  
## <a name="see-also"></a>Viz také  
 [Systém typů](../cppcx/type-system-c-cx.md)   
 [Referenční dokumentace jazyka Visual C++](../cppcx/visual-c-language-reference-c-cx.md)   
 [Odkaz na obory názvů](../cppcx/namespaces-reference-c-cx.md)