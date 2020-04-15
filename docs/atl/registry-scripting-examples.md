---
title: Příklady skriptování registru
ms.date: 11/04/2016
helpviewer_keywords:
- scripting, examples
- registrar scripts [ATL]
- scripts, Registrar scripts
- registry, Registrar
ms.assetid: b6df80e1-e08b-40ee-9243-9b381b172460
ms.openlocfilehash: 7bcdb7076982e2f0bd08f4fd82bb45f21e61ef20
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329331"
---
# <a name="registry-scripting-examples"></a>Příklady skriptování registru

Příklady skriptování v tomto tématu ukazují, jak přidat klíč do systémového registru, zaregistrovat server COM registrátora a zadat více stromů analýzy.

## <a name="add-a-key-to-hkey_current_user"></a>Přidání klíče k HKEY_CURRENT_USER

Následující strom analýzy ilustruje jednoduchý skript, který přidá jeden klíč do systémového registru. Skript zejména přidá klíč , `MyVeryOwnKey`do `HKEY_CURRENT_USER`. Také přiřadí výchozí hodnotu `HowGoesIt` řetězce nového klíče:

```
HKEY_CURRENT_USER
{
    'MyVeryOwnKey' = s 'HowGoesIt'
}
```

Tento skript lze snadno rozšířit definovat více podklíčů takto:

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

Nyní skript přidá podklíč `HasASubkey`, `MyVeryOwnKey`do . K tomuto podklíči `PrettyCool` přidá podklíč (s výchozí `DWORD` hodnotou `ANameValue` 55) i pojmenovanou hodnotu (s řetězcovou `WithANamedValue`hodnotou).

## <a name="register-the-registrar-com-server"></a><a name="_atl_register_the_registrar_com_server"></a>Registrace serveru COM registrátora

Následující skript registruje samotný server COM registrátora.

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

V době běhu tento strom `ATL.Registrar` analýzy `HKEY_CLASSES_ROOT`přidá klíč . K tomuto novému klíči pak:

- Určuje `ATL Registrar Class` jako výchozí hodnotu řetězce klíče.

- Přidá `CLSID` jako podklíč.

- Určuje `{44EC053A-400F-11D0-9DCD-00A0C90391D3}` pro `CLSID`soubor . (Tato hodnota je CLSID registrátora `CoCreateInstance`pro použití s .)

Vzhledem k tomu, `CLSID` že je sdílena, by neměla být odebrána v režimu Zrušení registrace. Příkaz , `NoRemove CLSID`provede to tím, `CLSID` že označuje, že by měl být otevřen v režimu Register a ignorován v režimu Zrušení registrace.

Příkaz `ForceRemove` poskytuje funkci úklidu odebráním klíče a všech jeho podklíčů před opětovným vytvořením klíče. To může být užitečné, pokud se změnily názvy podklíčů. V tomto příkladu `ForceRemove` skriptování `{44EC053A-400F-11D0-9DCD-00A0C90391D3}` zkontroluje, zda již existuje. Pokud ano, `ForceRemove`:

- Rekurzivně odstraní `{44EC053A-400F-11D0-9DCD-00A0C90391D3}` a všechny jeho podklíče.

- Znovu vytvoří `{44EC053A-400F-11D0-9DCD-00A0C90391D3}`.

- Přidá `ATL Registrar Class` jako výchozí hodnotu řetězce pro `{44EC053A-400F-11D0-9DCD-00A0C90391D3}`aplikace .

Strom analýzy nyní přidá dva `{44EC053A-400F-11D0-9DCD-00A0C90391D3}`nové podklíče . První klíč `ProgID`, získá výchozí hodnotu řetězce, která je ProgID. Druhý klíč `InprocServer32`, získá výchozí hodnotu řetězce , `%MODULE%`to je hodnota preprocesoru vysvětlená v části Použití [nahraditelných parametrů (Preprocesor registrátora)](../atl/using-replaceable-parameters-the-registrar-s-preprocessor.md)tohoto článku. `InprocServer32`také získá pojmenovanou hodnotu `ThreadingModel`, `Apartment`s řetězcovou hodnotou .

## <a name="specify-multiple-parse-trees"></a>Určení více stromů analýzy

Chcete-li zadat více než jeden strom analýzy ve skriptu, jednoduše umístěte jeden strom na konec jiného. Například následující skript přidá klíč `MyVeryOwnKey`, do stromů analýzy pro obě `HKEY_CLASSES_ROOT` a `HKEY_CURRENT_USER`:

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
> Ve skriptu registrátora je maximální velikost tokenu 4K. (Token je libovolný rozpoznatelný prvek v syntaxi.) V předchozím příkladu `HKCR`skriptování `'MyVeryOwnKey'`, `'HowGoesIt'` `HKEY_CURRENT_USER`, , a jsou všechny tokeny.

## <a name="see-also"></a>Viz také

[Vytváření skriptů registrátora](../atl/creating-registrar-scripts.md)
