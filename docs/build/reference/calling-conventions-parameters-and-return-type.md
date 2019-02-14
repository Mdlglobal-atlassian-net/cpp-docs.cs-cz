---
title: Konvence volání, parametry a návratový typ
ms.date: 02/13/2019
helpviewer_keywords:
- calling conventions, helper functions
- helper functions, calling conventions
- helper functions, return types
ms.assetid: 0ffa4558-6005-4803-be95-7a8ec8837660
ms.openlocfilehash: 15631b305246cbfd7dcd8081cb1ee488bf225fec
ms.sourcegitcommit: eb2b34a24e6edafb727e87b138499fa8945f981e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2019
ms.locfileid: "56264800"
---
# <a name="calling-conventions-parameters-and-return-type"></a>Konvence volání, parametry a návratový typ

Pomocná rutina prototypem je:

```
FARPROC WINAPI __delayLoadHelper2(
    PCImgDelayDescr pidd,
    FARPROC * ppfnIATEntry
);
```

### <a name="parameters"></a>Parametry

*pidd*<br/>
A `const` ukazatel `ImgDelayDescr` posuny různých dat týkajících se importu, časové razítko pro informace o vazbě a sadu atributů, které poskytují další informace o obsahu, popisovač, který obsahuje. V současné době neexistuje pouze jeden atribut `dlattrRva`, což znamená, že jsou adresy v popisovači relativních virtuálních adres. Další informace najdete v tématu deklarace v *delayimp.h*.

Pro definici `PCImgDelayDescr` struktury, přečtěte si téma [struktura a definice konstant](../../build/reference/structure-and-constant-definitions.md).

*ppfnIATEntry*<br/>
Ukazatel pozice v zpoždění načtení tabulky importních adres (IAT), který se aktualizuje s adresou importované funkce. Pomocná rutina musí ukládat stejnou hodnotu, která se vrátí do tohoto umístění.

## <a name="expected-return-values"></a>Byl očekáván návratové hodnoty

Pokud je funkce úspěšná, vrátí adresu importované funkce.

Pokud funkce selže, vyvolá výjimku a vrátí hodnotu 0. Může být vyvolána oznámením tři druhy výjimek:

- Neplatný parametr, který se stane, když na atributy v `pidd` nejsou zadané správně.

- `LoadLibrary` v zadané knihovně DLL se nezdařilo.

- Selhání `GetProcAddress`.

Je vaší odpovědností, abyste tyto výjimky zpracovat.

## <a name="remarks"></a>Poznámky

Je konvence volání pro pomocnou funkci `__stdcall`. Typ vrácené hodnoty není relevantní, a proto se používá FARPROC. Tato funkce má C-linkage.

Návratová hodnota pomocné rutiny zatížení zpoždění musí být uložen v umístění ukazatel předaný funkci, pokud chcete, aby vaše pomocná rutina má být použit jako hák oznámení. V takovém případě je odpovědný za vyhledání procesoru příslušnou funkci ukazatel k vrácení kódu. Převodní rutina kód, který generuje propojovací program poté přebírá tento návratovou hodnotu jako skutečné cíl importu a přejde přímo do ní.

## <a name="sample"></a>Ukázka

Následující kód ukazuje, jak implementovat funkci jednoduchých připojení.

```C
FARPROC WINAPI delayHook(unsigned dliNotify, PDelayLoadInfo pdli)
{
    switch (dliNotify) {
        case dliStartProcessing :

            // If you want to return control to the helper, return 0.
            // Otherwise, return a pointer to a FARPROC helper function
            // that will be used instead, thereby bypassing the rest
            // of the helper.

            break;

        case dliNotePreLoadLibrary :

            // If you want to return control to the helper, return 0.
            // Otherwise, return your own HMODULE to be used by the
            // helper instead of having it call LoadLibrary itself.

            break;

        case dliNotePreGetProcAddress :

            // If you want to return control to the helper, return 0.
            // If you choose you may supply your own FARPROC function
            // address and bypass the helper's call to GetProcAddress.

            break;

        case dliFailLoadLib :

            // LoadLibrary failed.
            // If you don't want to handle this failure yourself, return 0.
            // In this case the helper will raise an exception
            // (ERROR_MOD_NOT_FOUND) and exit.
            // If you want to handle the failure by loading an alternate
            // DLL (for example), then return the HMODULE for
            // the alternate DLL. The helper will continue execution with
            // this alternate DLL and attempt to find the
            // requested entrypoint via GetProcAddress.

            break;

        case dliFailGetProc :

            // GetProcAddress failed.
            // If you don't want to handle this failure yourself, return 0.
            // In this case the helper will raise an exception
            // (ERROR_PROC_NOT_FOUND) and exit.
            // If you choose you may handle the failure by returning
            // an alternate FARPROC function address.

            break;

        case dliNoteEndProcessing :

            // This notification is called after all processing is done.
            // There is no opportunity for modifying the helper's behavior
            // at this point except by longjmp()/throw()/RaiseException.
            // No return value is processed.

            break;

        default :

            return NULL;
    }

    return NULL;
}

/*
and then at global scope somewhere
const PfnDliHook __pfnDliNotifyHook2 = delayHook;
*/
```

## <a name="see-also"></a>Viz také:

[Základní informace o podpůrné funkci](../../build/reference/understanding-the-helper-function.md)