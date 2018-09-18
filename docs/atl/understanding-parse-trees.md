---
title: Registrátor ATL a stromů analýzy | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- parse trees
ms.assetid: 668ce2dd-a1c3-4ca0-8135-b25267cb6a85
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 08c92d86cbbfd38ed4ae852ce52e3b70735812e9
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46028087"
---
# <a name="understanding-parse-trees"></a>Principy stromů analýzy

Můžete definovat jeden nebo více stromů analýzy ve skriptu registrátoru, kde každý strom analýzy má následující formát:

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
<Add Key> ::= [ForceRemove | NoRemove | val]<Key Name> [<Key Value>][{<Add Key>}]
<Delete Key> ::= Delete<Key Name>
<Key Name> ::= '<AlphaNumeric>+'
<AlphaNumeric> ::= any character not NULL, i.e. ASCII 0
<Key Value> ::== <Key Type><Key Name>
<Key Type> ::= s | d
<Key Value> ::= '<AlphaNumeric>'
```

> [!NOTE]
> `HKEY_CLASSES_ROOT` a `HKCR` jsou ekvivalentní; `HKEY_CURRENT_USER` a `HKCU` jsou ekvivalentní; a tak dále.

Strom analýzy můžete přidat více klíčů a podklíče \<kořenového klíče >. Přitom, uchová podklíč popisovač otevřené až analyzátor byla dokončena analýza všem příslušným podklíčům. Tento přístup je efektivnější než pracující na jeden klíč najednou, jak je znázorněno v následujícím příkladu:

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

Tady doménový Registrátor zpočátku otevře (vytvoří) `HKEY_CLASSES_ROOT\MyVeryOwnKey`. Pak uvidí, který `MyVeryOwnKey` obsahuje podklíč. Místo klíč, který chcete zavřít `MyVeryOwnKey`, doménový Registrátor uchovává popisovač a otevře (vytvoří) `HasASubKey` pomocí tohoto úchytu nadřazené. (Systémového registru může být pomalejší při otevření bez nadřazené popisovač.) Proto otevírání `HKEY_CLASSES_ROOT\MyVeryOwnKey` a poté otevřou `HasASubKey` s `MyVeryOwnKey` je rychlejší než otevření nadřazené `MyVeryOwnKey`uzavřen `MyVeryOwnKey`a poté otevřou `MyVeryOwnKey\HasASubKey`.

## <a name="see-also"></a>Viz také

[Vytváření skriptů registrátoru](../atl/creating-registrar-scripts.md)

