---
title: Vyřazování typů a členů (C + +/ CX) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: language-reference
ms.assetid: b20b01c1-a439-4ff0-8cf3-d7280c492813
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8aecb47db6e9d620ff49fac337454242a1bdb72a
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42605698"
---
# <a name="deprecating-types-and-members-ccx"></a>Vyřazování typů a členů (C + +/ CX)
V jazyce C + +/ CX, vyřazení prostředí Windows Runtime typů a členů pro producenty a spotřebiteli pomocí [zastaralé](http://msdn.microsoft.com/en-us/8b02ad36-3b5f-4361-888b-e6a99040e57c) je atribut podporovaný. Využití rozhraní API, ke kterému tento atribut používá, dostanete zprávu upozornění kompilace, která označuje, že rozhraní API je zastaralé a také doporučuje alternativní rozhraní API pro použití. Ve vlastní veřejné typy a metody můžete použít tento atribut a zadejte vlastní zprávu.  
  
> [!CAUTION]
>  [Zastaralé](http://msdn.microsoft.com/en-us/8b02ad36-3b5f-4361-888b-e6a99040e57c) atribut lze použít pouze s typy Windows Runtime. Standardní C++ tříd a členů, použijte [__declspec(deprecated)](http://msdn.microsoft.com/library/044swk7y.aspx).  
  
### <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak přestat používat vaše vlastní veřejné rozhraní API – například v součásti prostředí Windows Runtime. Druhý operátor typu [Windows: Foundation:: Metadata::DeprecationType](http://msdn.microsoft.com/en-us/ee01e63d-37d0-4273-accc-fca174f88bfa) Určuje, jestli je rozhraní API je zastaralé nebo odebrán. Aktuálně pouze DeprecationType::Deprecated hodnota nepodporuje. Třetí parametr v atributu určuje, [Windows::Foundation::Metadata::Platform](http://msdn.microsoft.com/en-us/1eae292d-1ab7-4d97-a58c-b0beffd51ef5) pro kterou platí atribut.  
  
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
|Ovládací prvek XAML|  
|delegát|  
|event|  
|pole|  
|enum|  
|struct |  
|– metoda|  
|třída|  
|rozhraní|  
|property|  
|pole – struktura|  
|konstruktorem s parametry|  
  
## <a name="see-also"></a>Viz také  
 [Systém typů](../cppcx/type-system-c-cx.md)   
 [Referenční dokumentace jazyka Visual C++](../cppcx/visual-c-language-reference-c-cx.md)   
 [Odkaz na obory názvů](../cppcx/namespaces-reference-c-cx.md)