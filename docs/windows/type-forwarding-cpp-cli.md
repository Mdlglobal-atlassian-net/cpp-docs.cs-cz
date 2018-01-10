---
title: "Předávání typů (C + +/ CLI) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords: type forwarding, Visual C++
ms.assetid: ae730b69-0c27-41cc-84e1-3132783866ea
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6898c011a4e2e907cd745ccb206b0e0f0b37e78f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="type-forwarding-ccli"></a>Předávání typů (C++/CLI)
*Předávání typů* umožňuje přesunout typu z jednoho sestavení (sestavení A) do jiné sestavení (sestavení B), tak, aby ji není nutné znovu zkompiluje klienty, kteří sestavení A.  
  
## <a name="all-platforms"></a>Všechny platformy  
 Tato funkce není podporována v všechny moduly runtime.  
  
## <a name="windows-runtime"></a>prostředí Windows Runtime  
 Tato funkce není podporována v prostředí Windows Runtime.  
  
### <a name="requirements"></a>Požadavky  
 – Možnost kompilátoru: **/ZW**  
  
## <a name="common-language-runtime"></a>CLR (Common Language Runtime)  
 Následující příklad kódu ukazuje, jak používat předávání typů.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
#using "new.dll"  
[assembly:TypeForwardedTo(type::typeid)];  
```  
  
### <a name="parameters"></a>Parametry  
 `new`  
 Sestavení, do které přesouváte definici typu.  
  
 `type`  
 Typ, jejichž definice přesouváte do jiné sestavení.  
  
### <a name="remarks"></a>Poznámky  
 Když se dodává součást (sestavení) a je používán klientské aplikace, můžete použít typ předávání přesunout typem z komponenty (sestavení) do jiné sestavení, dodávat aktualizované součásti (a všechny další sestavení požadovaná) a klientem aplikace budou i nadále fungovat bez probíhá zopakovat.  
  
 Předávání typů funguje výhradně u součástí odkazuje stávající aplikace. Když znovu vytvoříte aplikaci, musí být odkazy na příslušné sestavení pro všechny typy používané v aplikaci.  
  
 Při předávání typu (typu A) ze sestavení, je nutné přidat `TypeForwardedTo` atribut pro tento typ, stejně jako odkaz na sestavení. Sestavení, na kterou odkazujete musí obsahovat jeden z následujících akcí:  
  
-   Definice pro typ A.  
  
-   A `TypeForwardedTo` atribut typu A, stejně jako odkaz na sestavení.  
  
 Mezi příklady typů, které může být přeposílán patří:  
  
-   REF – třídy  
  
-   Hodnota třídy  
  
-   výčty  
  
-   rozhraní  
  
 Tyto typy nemohou předat dál:  
  
-   Obecné typy  
  
-   Nativní typy  
  
-   Vnořené typy (Pokud chcete předat dál vnořené typy, by měla předávat nadřazených typů)  
  
 Typ může předávat na sestavení vytvořené v libovolném jazyce cílení na modul common language runtime.  
  
 Takže pokud se soubor zdrojového kódu, který je použit k vytvoření sestavení A.dll obsahuje definici typu (`ref class MyClass`), a chcete přesunout typu definice sestavení B.dll byste:  
  
1.  Přesunout `MyClass` definic k souboru zdrojového kódu, sloužící k vytvoření B.dll typu.  
  
2.  Sestavení sestavení B.dll  
  
3.  Odstranit `MyClass` zadejte definici z zdrojový kód používá k vytvoření A.dll a nahraďte ji následujícím kódem:  
  
    ```  
    #using "B.dll"  
    [assembly:TypeForwardedTo(MyClass::typeid)];  
    ```  
  
4.  Vytvořte sestavení A.dll.  
  
5.  Použijte A.dll bez nutnosti rekompilace klientské aplikace.  
  
### <a name="requirements"></a>Požadavky  
 – Možnost kompilátoru:   **/CLR**