---
title: Registrátor ATL a stromy analýz
ms.date: 11/04/2016
helpviewer_keywords:
- parse trees
ms.assetid: 668ce2dd-a1c3-4ca0-8135-b25267cb6a85
ms.openlocfilehash: de2cea9b0e7b7c62236f708f9aa8217eaa5df51d
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/27/2020
ms.locfileid: "82168693"
---
# <a name="understanding-parse-trees"></a>Principy stromů analýzy

Ve svém skriptu registrátora můžete definovat jednu nebo více stromů analýz, kde každý strom analýz má následující tvar:

> \<kořenový klíč> {\<výraz registru>} +

kde:

> \<> kořenového klíče:: = HKEY_CLASSES_ROOT | HKEY_CURRENT_USER | \
> &nbsp;&nbsp;&nbsp;&nbsp;HKEY_LOCAL_MACHINE | HKEY_USERS | \
> &nbsp;&nbsp;&nbsp;&nbsp;HKEY_PERFORMANCE_DATA | HKEY_DYN_DATA | \
> &nbsp;&nbsp;&nbsp;&nbsp;HKEY_CURRENT_CONFIG | HKCR | HKCU | \
> &nbsp;&nbsp;&nbsp;&nbsp;HKLM | HKU | HKPD | HKDD | HKCC

> \<výraz registru>:: = \<přidat klíčovou> | \<Odstranit> klíčů

> \<Přidat klíčovou>:: =**[ForceRemove** | **. Remove** | **Val**\<] název klíče>\<[hodnota klíče>] [\<{Add Key>}]

> \<Odstranit klíč>:: = **Odstranit**\<název klíče>

> \<Název klíče>:: = **'**\<alfanumerické>+**'**

> \<Alfanumerické>:: = *libovolný znak není null, tj. ASCII 0*

> \<Hodnota klíče>:: = \<typ klíče>\<název klíče>

> \<Typ klíče>:: = **s** | **d**

> \<Hodnota klíče>:: = **'**\<alfanumerický>**'**

> [!NOTE]
> `HKEY_CLASSES_ROOT`a `HKCR` jsou ekvivalentní; `HKEY_CURRENT_USER` a `HKCU` jsou ekvivalentní; a tak dále.

Strom analýzy může přidat více klíčů a podklíčů do \<kořenového klíče>. V takovém případě udržuje popisovač podklíče otevřený, dokud analyzátor nedokončí analýzu všech jeho podklíčů. Tento přístup je efektivnější než provoz na jednom klíči, jak je vidět v následujícím příkladu:

```rgs
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

Tady se zpočátku otevře registrátor (vytvoří) `HKEY_CLASSES_ROOT\MyVeryOwnKey`. Pak uvidí, že `MyVeryOwnKey` obsahuje podklíč. Místo toho, aby `MyVeryOwnKey`se klíč zavřel, registrátor zachová popisovač a otevře (vytvoří) `HasASubKey` pomocí tohoto nadřazeného popisovače. (Systémový registr může být pomalejší, pokud není otevřený žádný nadřazený popisovač.) Proto je otevření `HKEY_CLASSES_ROOT\MyVeryOwnKey` a pak otevření `HasASubKey` s `MyVeryOwnKey` nadřazeným objektem rychlejší než otevírání `MyVeryOwnKey`, zavírání `MyVeryOwnKey`a pak otevírání `MyVeryOwnKey\HasASubKey`.

## <a name="see-also"></a>Viz také

[Vytváření skriptů registrátora](../atl/creating-registrar-scripts.md)
