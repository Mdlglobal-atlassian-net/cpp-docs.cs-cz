---
title: Předávání typů (C + +/ CLI) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- type forwarding, Visual C++
ms.assetid: ae730b69-0c27-41cc-84e1-3132783866ea
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 627b0a881795a963e3739accc351ee684b7b8232
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/08/2018
ms.locfileid: "39644931"
---
# <a name="type-forwarding-ccli"></a>Předávání typů (C++/CLI)
*Předávání typů* vám umožní přesunout typ z jednoho sestavení (assembly A) do jiné sestavení (assembly B), takže není nutné znovu zkompilovat klienty, kteří využívají sestavení A.  
  
## <a name="all-platforms"></a>Všechny platformy  
 Tato funkce není podporována v všechny moduly runtime.  
  
## <a name="windows-runtime"></a>prostředí Windows Runtime  
 Tato funkce není podporována v modulu Windows Runtime.  
  
### <a name="requirements"></a>Požadavky  
 – Možnost kompilátoru: `/ZW`  
  
## <a name="common-language-runtime"></a>CLR (Common Language Runtime)  
 Následující příklad kódu ukazuje, jak používat předávání typů.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
#using "new.dll"  
[assembly:TypeForwardedTo(type::typeid)];  
```  
  
### <a name="parameters"></a>Parametry  
 *new*  
 Sestavení, do kterého se přesunutí definice typu.  
  
 *Typ*  
 Typ, jejichž definice jsou přesunu do jiného sestavení.  
  
### <a name="remarks"></a>Poznámky  
 Poté, co se dodává komponentu (sestavení) a je používán klientskými aplikacemi, můžete použít typ předávání k přesunutí typu do jiného sestavení z komponenty (sestavení), dodejte aktualizované součásti (a jakékoli další požadovaná sestavení) a klient aplikace budou i nadále fungovat bez se znovu zkompilovat.  
  
 Předávání typů funguje jenom pro součásti odkazují stávající aplikace. Při opětovném sestavování aplikace, musí být odkazy na odpovídající sestavení pro všechny typy použité v aplikaci.  
  
 Při předávání typu (typ A) ze sestavení, je nutné přidat `TypeForwardedTo` atributů pro daný typ, stejně jako odkaz na sestavení. Sestavení, na které odkazujete musí obsahovat jeden z následujících akcí:  
  
-   Definice pro typ A.  
  
-   A `TypeForwardedTo` atributu pro typ A také odkaz na sestavení.  
  
 Mezi příklady typů, které může být přeposílán patří:  
  
-   referenční třídy  
  
-   Hodnota třídy  
  
-   výčty  
  
-   rozhraní  
  
 Tyto typy nemohou předat dál:  
  
-   Obecné typy  
  
-   Nativní typy  
  
-   Vnořené typy (Pokud chcete dál vnořený typ, by měl dál nadřazeného typu.)  
  
 Typ lze předat sestavení vytvořené v libovolném jazyce cílení na modul common language runtime.  
  
 Pokud soubor zdrojového kódu, který se používá k vytvoření sestavení A.dll obsahuje definici typu tedy (`ref class MyClass`), a chtěli jste typu přesuňte definice sestavení B.dll byste:  
  
1.  Přesunout `MyClass` definice do souboru zdrojového kódu slouží k sestavení B.dll typu.  
  
2.  Sestavení B.dll  
  
3.  Odstranit `MyClass` zadejte definici ze zdrojového kódu, používá k vytvoření A.dll a nahraďte následujícím kódem:  
  
    ```  
    #using "B.dll"  
    [assembly:TypeForwardedTo(MyClass::typeid)];  
    ```  
  
4.  Sestavení A.dll.  
  
5.  Použití A.dll bez opětovné kompilace klientských aplikací.  
  
### <a name="requirements"></a>Požadavky  
 – Možnost kompilátoru: `/clr`