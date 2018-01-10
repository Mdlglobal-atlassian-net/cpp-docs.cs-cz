---
title: "Příklady skriptování registru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- scripting, examples
- registrar scripts [ATL]
- scripts, Registrar scripts
- registry, Registrar
ms.assetid: b6df80e1-e08b-40ee-9243-9b381b172460
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 1b2a5dfd3bd31674917a5b41174277ef787aff25
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="registry-scripting-examples"></a>Příklady skriptování registru
Skriptovací příklady v tomto tématu ukazují, jak přidat klíč registru systému, zaregistrujte server COM registrátora a zadejte více stromy analýzy.  
  
## <a name="add-a-key-to-hkeycurrentuser"></a>Přidá klíč do HKEY_CURRENT_USER  
 Následující strom analýzy znázorňuje jednoduché skript, který přidá jeden klíč registru systému. Konkrétně skript přidá klíč, `MyVeryOwnKey`do `HKEY_CURRENT_USER`. Také přiřadí výchozí hodnotu řetězce `HowGoesIt` do nového klíče:  
  
```  
HKEY_CURRENT_USER  
{  
 'MyVeryOwnKey' = s 'HowGoesIt'  
}  
```  
  
 Tento skript lze snadno rozšířit k definování více podklíče následujícím způsobem:  
  
```  
HKCU  
{  
 'MyVeryOwnKey' = s 'HowGoesIt'  
 {  
 'HasASubkey'  
 {  
 'PrettyCool' = d '55'  
    val 'ANameValue' = s 'WithANamedValue'  
 }  
 }  
}  
```  
  
 Nyní, skript přidá podklíč, `HasASubkey`do `MyVeryOwnKey`. Na tento podklíč, přidá, i `PrettyCool` podklíč (s výchozí `DWORD` hodnotu 55) a `ANameValue` s názvem hodnotu (s řetězcovou hodnotu `WithANamedValue`).  
  
##  <a name="_atl_register_the_registrar_com_server"></a>Registrace serveru registrátora COM  
 Následující skript zaregistruje samotný server COM registrátora.  
  
```  
HKCR  
{  
    ATL.Registrar = s 'ATL Registrar Class'  
 {  
    CLSID = s '{44EC053A-400F-11D0-9DCD-00A0C90391D3}'  
 }  
    NoRemove CLSID  
 {  
    ForceRemove {44EC053A-400F-11D0-9DCD-00A0C90391D3} = 
    s 'ATL Registrar Class'  
 {  
    ProgID = s 'ATL.Registrar'  
    InprocServer32 = s '%MODULE%'  
 {  
    val ThreadingModel = s 'Apartment'  
 }  
 }  
 }  
}  
```  
  
 V době běhu, přidá tento strom analýzy `ATL.Registrar` klíče na `HKEY_CLASSES_ROOT`. Pro tento nový klíč pak it:  
  
-   Určuje `ATL Registrar Class` jako klíče výchozí hodnotu řetězce.  
  
-   Přidá `CLSID` jako podklíč.  
  
-   Určuje `{44EC053A-400F-11D0-9DCD-00A0C90391D3}` pro `CLSID`. (Tato hodnota je vašeho registrátora CLSID pro použití s `CoCreateInstance`.)  
  
 Protože `CLSID` je sdílená, neměla by být odebrána v režimu Unregister. Příkaz `NoRemove CLSID`, tím označující, že `CLSID` by měla otevřít v režimu registrace a ignorovat v režimu Unregister.  
  
 `ForceRemove` Příkaz poskytuje funkce housekeeping odebráním klíče a jeho podklíčů před znovu vytvořit klíč. To může být užitečné, pokud se změnily názvy podklíčů. V tomto příkladu skriptování `ForceRemove` kontroluje, pokud `{44EC053A-400F-11D0-9DCD-00A0C90391D3}` již existuje. Pokud ano, `ForceRemove`:  
  
-   Odstraní rekurzivně `{44EC053A-400F-11D0-9DCD-00A0C90391D3}` a všechny jeho podklíče.  
  
-   Znovu vytvoří `{44EC053A-400F-11D0-9DCD-00A0C90391D3}`.  
  
-   Přidá `ATL Registrar Class` jako výchozí hodnotu řetězce pro `{44EC053A-400F-11D0-9DCD-00A0C90391D3}`.  
  
 Strom analýzy teď přidá dva nové podklíče k `{44EC053A-400F-11D0-9DCD-00A0C90391D3}`. První klíč `ProgID`, získá výchozí hodnotu řetězce, který je identifikátor ProgID. Druhý klíč `InprocServer32`, získá výchozí hodnotu řetězce `%MODULE%`, která je hodnotu preprocesoru popsané v části [pomocí nahraditelné parametry (registrátora Preprocessor)](../atl/using-replaceable-parameters-the-registrar-s-preprocessor.md), tohoto článku. `InprocServer32`také získá hodnotu s názvem `ThreadingModel`, s řetězcovou hodnotu `Apartment`.  
  
## <a name="specify-multiple-parse-trees"></a>Zadejte více stromy analýzy  
 Pokud chcete zadat více než jeden strom analýzy ve skriptu, umístíte na konci jiné jeden stromu. Například následující skript přidá klíč, `MyVeryOwnKey`, k analýze stromy pro obě `HKEY_CLASSES_ROOT` a `HKEY_CURRENT_USER`:  
  
```  
HKCR  
{  
 'MyVeryOwnKey' = s 'HowGoesIt'  
}  
HKEY_CURRENT_USER  
{  
 'MyVeryOwnKey' = s 'HowGoesIt'  
}  
```  
  
> [!NOTE]
>  Ve skriptu registrátora 4K je maximální velikost tokenu. (Token je libovolný rozpoznatelném element v syntaxi.) V předchozím příkladu skriptování `HKCR`, `HKEY_CURRENT_USER`, `'MyVeryOwnKey'`, a `'HowGoesIt'` jsou všechny tokeny.  
  
## <a name="see-also"></a>Viz také  
 [Vytváření skriptů registrátoru](../atl/creating-registrar-scripts.md)

