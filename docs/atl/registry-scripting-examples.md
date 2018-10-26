---
title: Příklady skriptování registru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- scripting, examples
- registrar scripts [ATL]
- scripts, Registrar scripts
- registry, Registrar
ms.assetid: b6df80e1-e08b-40ee-9243-9b381b172460
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1e15d05be30b4343649e4866fbbea27e914dc320
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50068382"
---
# <a name="registry-scripting-examples"></a>Příklady skriptování registru

Příklady skriptování v tomto tématu ukazují, jak přidá klíč do systémového registru, zaregistrujte server registrátora COM a zadat více stromů analýzy.

## <a name="add-a-key-to-hkeycurrentuser"></a>Přidá klíč do klíče HKEY_CURRENT_USER

Následující strom analýzy ukazuje jednoduchý skript, který přidá jeden klíč do systémového registru. Konkrétně se skript přidá klíč, `MyVeryOwnKey`do `HKEY_CURRENT_USER`. Také přiřadí výchozí řetězcovou hodnotu `HowGoesIt` do nového klíče:

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

Nyní, skript přidá podklíč, `HasASubkey`do `MyVeryOwnKey`. Tento podklíč obě přidá `PrettyCool` podklíč (s výchozí `DWORD` hodnotu 55) a `ANameValue` se pojmenovaná hodnota (s řetězcovou hodnotu `WithANamedValue`).

##  <a name="_atl_register_the_registrar_com_server"></a> Registrace serveru COM doménový Registrátor

Následující skript zaregistruje samotný server COM doménový Registrátor.

```
HKCR
{
    ATL.Registrar = s 'ATL Registrar Class'
    {
        CLSID = s '{44EC053A-400F-11D0-9DCD-00A0C90391D3}'
    }
    NoRemove CLSID
    {
        ForceRemove {44EC053A-400F-11D0-9DCD-00A0C90391D3} = s 'ATL Registrar Class'
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

V době běhu, přidá tento strom analýzy `ATL.Registrar` klíč `HKEY_CLASSES_ROOT`. Na tento nový klíč pak it:

- Určuje `ATL Registrar Class` jako výchozí hodnotu řetězce klíče.

- Přidá `CLSID` jako podklíč.

- Určuje `{44EC053A-400F-11D0-9DCD-00A0C90391D3}` pro `CLSID`. (Tato hodnota je vašeho registrátora CLSID pro použití s `CoCreateInstance`.)

Protože `CLSID` je sdílen, neměla by být odebrána v režimu odregistrovat. Příkaz `NoRemove CLSID`, tím označující, že `CLSID` by mělo být otevřen v režimu registrace a ignoruje v režimu odregistrovat.

`ForceRemove` Příkaz poskytuje funkce údržbu tak, že odeberete klíč a všem příslušným podklíčům před opětovné vytvoření klíče. To může být užitečné, pokud se názvy podklíčů změnily. V tomto příkladu skriptovací `ForceRemove` kontroluje, jestli `{44EC053A-400F-11D0-9DCD-00A0C90391D3}` již existuje. Pokud ano, `ForceRemove`:

- Rekurzivně odstraní `{44EC053A-400F-11D0-9DCD-00A0C90391D3}` a všem příslušným podklíčům.

- Znovu vytvoří `{44EC053A-400F-11D0-9DCD-00A0C90391D3}`.

- Přidá `ATL Registrar Class` jako výchozí hodnotu řetězce pro `{44EC053A-400F-11D0-9DCD-00A0C90391D3}`.

Strom analýzy teď přidá dva nové podklíče `{44EC053A-400F-11D0-9DCD-00A0C90391D3}`. První klíč `ProgID`, získá výchozí hodnotu řetězce, který je identifikátor ProgID. Druhý klíč `InprocServer32`, získá výchozí hodnotu řetězce `%MODULE%`, která je hodnotu preprocesoru je popsáno v části [použití nahraditelných parametrů (preprocesor The registrátoru)](../atl/using-replaceable-parameters-the-registrar-s-preprocessor.md), část tohoto článku. `InprocServer32` Pojmenovaná hodnota, získá také `ThreadingModel`, s řetězcovou hodnotu `Apartment`.

## <a name="specify-multiple-parse-trees"></a>Zadejte více stromů analýzy

Pokud chcete zadat více než jeden strom analýzy ve skriptu, umístíte na konci druhého jednom stromu. Například následující skript přidá klíč, `MyVeryOwnKey`, k stromů analýzy pro obě `HKEY_CLASSES_ROOT` a `HKEY_CURRENT_USER`:

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
> Ve skriptu registrátoru je 4 kB maximální velikost tokenu. (Token je libovolný prvek rozpoznat v syntaxi). V předchozím příkladu skriptovací `HKCR`, `HKEY_CURRENT_USER`, `'MyVeryOwnKey'`, a `'HowGoesIt'` jsou všechny tokeny.

## <a name="see-also"></a>Viz také

[Vytváření skriptů registrátoru](../atl/creating-registrar-scripts.md)

