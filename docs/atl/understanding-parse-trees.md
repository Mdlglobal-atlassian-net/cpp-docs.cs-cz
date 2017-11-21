---
title: "Registrátor ATL a analýzy stromy | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: parse trees
ms.assetid: 668ce2dd-a1c3-4ca0-8135-b25267cb6a85
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 091ad40625c85f465e3989dd2dff790c630f6538
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="understanding-parse-trees"></a>Principy analýzy stromů
Jeden nebo více stromy analýzy můžete definovat ve vašem Registrátor skriptu, kde každý strom analýzy má následující formát:  
  
```  
<root key>{<registry expression>}+  
```  
  
 kde:  
  
```  
<root key> ::= HKEY_CLASSES_ROOT | HKEY_CURRENT_USER |  
    HKEY_LOCAL_MACHINE | HKEY_USERS |  
    HKEY_PERFORMANCE_DATA | HKEY_DYN_DATA |  
    HKEY_CURRENT_CONFIG | HKCR | HKCU |  
    HKLM | HKU | HKPD | HKDD | HKCC  
<registry expression> ::= <Add Key> | <Delete Key>  
<Add Key> ::= [ForceRemove | NoRemove | val]<Key Name>  
 [<Key Value>][{<Add Key>}]  
<Delete Key> ::= Delete<Key Name>  
<Key Name> ::= '<AlphaNumeric>+'  
<AlphaNumeric> ::= any character not NULL, i.e. ASCII 0  
<Key Value> ::== <Key Type><Key Name>  
<Key Type> ::= s | d  
<Key Value> ::= '<AlphaNumeric>'  
```  
  
> [!NOTE]
> `HKEY_CLASSES_ROOT`a `HKCR` odpovídají; `HKEY_CURRENT_USER` a `HKCU` jsou ekvivalentní; a tak dále.  
  
 Strom analýzy můžete přidat více klíče a podklíčů k \<kořenový klíč >. Při tom udržuje podklíč popisovač otevřené až analyzátor po dokončení analýzy všechny jeho podklíče. Tento přístup je efektivnější než pracující na jeden klíč současně, jak je vidět v následujícím příkladu:  
  
```  
HKEY_CLASSES_ROOT  
{  
 'MyVeryOwnKey'  
 {  
 'HasASubKey'  
 {  
 'PrettyCool'  
 }  
 }  
}  
```  
  
 Zde původně otevře registrátora (vytvoří) `HKEY_CLASSES_ROOT\MyVeryOwnKey`. Pak uvidí, který `MyVeryOwnKey` obsahuje podklíč. Spíše než zavřete klíč k `MyVeryOwnKey`, registrátora uchovává popisovač a otevře (vytvoří) `HasASubKey` pomocí tohoto popisovače nadřazené. (Registr systému může být pomalejší v otevřeném žádný nadřazený popisovač.) Proto otevírání `HKEY_CLASSES_ROOT\MyVeryOwnKey` a pak otevřete `HasASubKey` s `MyVeryOwnKey` jako nadřazená položka rychlejší než otevírání `MyVeryOwnKey`, uzavření `MyVeryOwnKey`a pak otevřete `MyVeryOwnKey\HasASubKey`.  
  
## <a name="see-also"></a>Viz také  
 [Vytváření skripty registrátora](../atl/creating-registrar-scripts.md)

