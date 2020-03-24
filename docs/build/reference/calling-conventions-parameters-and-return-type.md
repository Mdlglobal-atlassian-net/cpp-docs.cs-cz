---
title: Konvence volání, parametry a návratový typ
ms.date: 02/13/2019
helpviewer_keywords:
- calling conventions, helper functions
- helper functions, calling conventions
- helper functions, return types
ms.assetid: 0ffa4558-6005-4803-be95-7a8ec8837660
ms.openlocfilehash: 90767141337512b053bb06a40823c4a22a8a4823
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80169744"
---
# <a name="calling-conventions-parameters-and-return-type"></a>Konvence volání, parametry a návratový typ

Prototyp rutiny pomocné rutiny:

```
FARPROC WINAPI __delayLoadHelper2(
    PCImgDelayDescr pidd,
    FARPROC * ppfnIATEntry
);
```

### <a name="parameters"></a>Parametry

*pidd*<br/>
`const` ukazatel na `ImgDelayDescr`, který obsahuje posun různých dat týkajících se importu, časové razítko pro informace o vazbě a sadu atributů, které poskytují další informace o obsahu deskriptoru. V současné době existuje pouze jeden atribut `dlattrRva`, který označuje, že adresy v popisovači jsou relativní virtuální adresy. Další informace najdete v tématu deklarace v *delayimp. h*.

Definice `PCImgDelayDescr` struktury viz [Definice struktury a konstanty](structure-and-constant-definitions.md).

*ppfnIATEntry*<br/>
Ukazatel na slot v tabulce adres importu zpožděného načtení (IAT), která je aktualizována adresou importované funkce. Pomocná rutina potřebuje Uložit stejnou hodnotu, kterou vrátí do tohoto umístění.

## <a name="expected-return-values"></a>Očekávané návratové hodnoty

Pokud je funkce úspěšná, vrátí adresu importované funkce.

Pokud funkce dojde k chybě, vyvolá výjimku a vrátí hodnotu 0. Je možné vyhodnotit tři typy výjimek:

- Neplatný parametr, který se stane, pokud nejsou správně zadány atributy v `pidd`.

- v zadané knihovně DLL se `LoadLibrary` nezdařila.

- Selhání `GetProcAddress`.

Je vaše zodpovědnost za zpracování těchto výjimek.

## <a name="remarks"></a>Poznámky

Konvence volání pomocné funkce je `__stdcall`. Typ návratové hodnoty není relevantní, takže se použije FARPROC. Tato funkce má propojení jazyka C.

Pokud nechcete, aby se rutina pomocníka použila jako zavěšení oznámení, musí být vrácená hodnota pomocníka pro odložené načítání uložená v umístění ukazatele na předané funkce. V takovém případě váš kód zodpovídá za nalezení vhodného ukazatele funkce, který se má vrátit. Kód zpětného volání, který linker vygeneruje, pak převezme tuto návratovou hodnotu jako skutečný cíl importu a přejde přímo na něj.

## <a name="sample"></a>Ukázka

Následující kód ukazuje, jak implementovat jednoduchou funkci zavěšení.

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

## <a name="see-also"></a>Viz také

[Základní informace o podpůrné funkci](understanding-the-helper-function.md)
