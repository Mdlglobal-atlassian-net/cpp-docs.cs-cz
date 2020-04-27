---
title: Příklady skriptování registru
ms.date: 11/04/2016
helpviewer_keywords:
- scripting, examples
- registrar scripts [ATL]
- scripts, Registrar scripts
- registry, Registrar
ms.assetid: b6df80e1-e08b-40ee-9243-9b381b172460
ms.openlocfilehash: 0e225ce28309aa619fd9436d8f4b93e60544e86c
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/27/2020
ms.locfileid: "82168745"
---
# <a name="registry-scripting-examples"></a>Příklady skriptování registru

Příklady skriptování v tomto tématu ukazují, jak přidat klíč do systémového registru, zaregistrovat server COM registrátora a zadat více stromů analýz.

## <a name="add-a-key-to-hkey_current_user"></a>Přidat klíč pro HKEY_CURRENT_USER

Následující strom analýzy znázorňuje jednoduchý skript, který do systémového registru přidá jeden klíč. Konkrétně skript přidá klíč, `MyVeryOwnKey`do. `HKEY_CURRENT_USER` Zároveň přiřadí výchozí hodnotu řetězce `HowGoesIt` k novému klíči:

```rgs
HKEY_CURRENT_USER
{
    'MyVeryOwnKey' = s 'HowGoesIt'
}
```

Tento skript lze snadno rozšířit, aby bylo možné definovat více podklíčů následujícím způsobem:

```rgs
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

Nyní skript přidá podklíč, `HasASubkey`do. `MyVeryOwnKey` Do tohoto podklíče `PrettyCool` přidá podklíč (s výchozí `DWORD` hodnotou 55) a `ANameValue` pojmenovanou hodnotu (s hodnotou řetězce `WithANamedValue`).

## <a name="register-the-registrar-com-server"></a><a name="_atl_register_the_registrar_com_server"></a>Registrace serveru COM registrátora

Následující skript registruje samotný registrátor serveru COM.

```rgs
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

V době běhu tento strom analýzy přidá `ATL.Registrar` klíč do. `HKEY_CLASSES_ROOT` Do tohoto nového klíče pak:

- Určuje `ATL Registrar Class` výchozí hodnotu řetězce klíče.

- Přidá `CLSID` jako podklíč.

- Určuje `{44EC053A-400F-11D0-9DCD-00A0C90391D3}` pro `CLSID`. (Tato hodnota je identifikátor CLSID registrátora pro použití s `CoCreateInstance`.)

Vzhledem `CLSID` k tomu, že je sdílena, neměla by být odebrána v režimu zrušení registrace. Příkaz `NoRemove CLSID`provede to tak, že označuje, že `CLSID` by měl být otevřen v režimu registru a ignorován v režimu zrušení registrace.

`ForceRemove` Příkaz poskytuje funkci údržbu odebráním klíče a všech jeho podklíčů před opětovným vytvořením klíče. To může být užitečné, pokud se názvy podklíčů změnily. V tomto příkladu skriptování aplikace `ForceRemove` kontroluje, zda `{44EC053A-400F-11D0-9DCD-00A0C90391D3}` již existuje. V `ForceRemove`takovém případě:

- Rekurzivně odstraní `{44EC053A-400F-11D0-9DCD-00A0C90391D3}` a všechny jeho podklíče.

- Znovu vytvoří `{44EC053A-400F-11D0-9DCD-00A0C90391D3}`.

- Přidá `ATL Registrar Class` jako výchozí hodnotu řetězce pro `{44EC053A-400F-11D0-9DCD-00A0C90391D3}`.

Strom analýzy nyní přidá dva nové podklíče do `{44EC053A-400F-11D0-9DCD-00A0C90391D3}`. První klíč `ProgID`Získá výchozí řetězcovou hodnotu, která je identifikátorem ProgID. Druhý klíč, `InprocServer32`, získá výchozí řetězcovou hodnotu `%MODULE%`, která je vysvětlená hodnota preprocesoru v části, [pomocí nahraditelných parametrů (preprocesor registrátora)](../atl/using-replaceable-parameters-the-registrar-s-preprocessor.md)tohoto článku. `InprocServer32`také získá pojmenovanou hodnotu `ThreadingModel`s řetězcovou hodnotou. `Apartment`

## <a name="specify-multiple-parse-trees"></a>Zadat více stromů analýz

Chcete-li zadat více než jeden strom analýzy ve skriptu, Stačí umístit jeden strom na konec jiného. Například následující skript přidá klíč, `MyVeryOwnKey`do stromů analýz pro obojí `HKEY_CLASSES_ROOT` a: `HKEY_CURRENT_USER`

```rgs
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
> V rámci skriptu registrátora je 4K maximální velikost tokenu. (Token je libovolný rozpoznatelný element v syntaxi.) V předchozích skriptovacích příkladech `HKCR` `HKEY_CURRENT_USER` `'MyVeryOwnKey'`,,, a `'HowGoesIt'` jsou všechny tokeny.

## <a name="see-also"></a>Viz také

[Vytváření skriptů registrátora](../atl/creating-registrar-scripts.md)
