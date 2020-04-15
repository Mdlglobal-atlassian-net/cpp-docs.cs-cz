---
title: mbrtowc
ms.date: 4/2/2020
api_name:
- mbrtowc
- _o_mbrtowc
api_location:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-convert-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- mbrtowc
helpviewer_keywords:
- mbrtowc function
ms.assetid: a1e87fcc-6de0-4ca1-bf26-508d28490286
ms.openlocfilehash: be46c3f3c728b70c7cbf060572acc24662637a81
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81340919"
---
# <a name="mbrtowc"></a>mbrtowc

Převeďte vícebajtový znak v aktuálním národním prostředí na ekvivalentní široký znak se schopností restartování uprostřed vícebajtového znaku.

## <a name="syntax"></a>Syntaxe

```C
size_t mbrtowc(
   wchar_t *wchar,
   const char *mbchar,
   size_t count,
   mbstate_t *mbstate
);
```

### <a name="parameters"></a>Parametry

*Wchar*<br/>
Adresa širokého znaku pro příjem převedeného širokého znakového řetězce (typ **wchar_t**). Tato hodnota může být ukazatel null, pokud není vyžadován žádný znak šířka vratky.

*mbchar*<br/>
Adresa posloupnosti bajtů (vícebajtový znak).

*Počet*<br/>
Počet bajtů ke kontrole.

*mbstate*<br/>
Ukazatel na objekt stavu převodu. Pokud je tato hodnota ukazatelem null, funkce používá statický objekt stavu vnitřního převodu. Vzhledem k tomu, že vnitřní **mbstate_t** objekt není bezpečný pro přístup z více vláken, doporučujeme vždy předat vlastní *argument mbstate.*

## <a name="return-value"></a>Návratová hodnota

Jedna z následujících hodnot:

0 Další *počet* nebo méně bajtů dokončit vícebajtový znak, který představuje null široký znak, který je uložen v *wchar*, pokud *wchar* není ukazatel null.

1 *počet*, včetně další *počet* nebo méně bajtů dokončit platný vícebajtový znak. Vrácená hodnota je počet bajtů, které doplňují vícebajtový znak. Široký znak ekvivalent je uložen v *wchar*, pokud *wchar* není ukazatel null.

(size_t) (-1) Došlo k chybě kódování. Další *počet* nebo méně bajtů nepřispívají k úplné a platné vícebajtový znak. V tomto případě **je chybné číslo** nastaveno na Hodnotu EILSEQ a stav posunu převodu ve *stavu mbstate* není určen.

(size_t) (-2) Další *počet* bajtů přispívají k neúplné, ale potenciálně platné vícebajtový znak a všechny *počet* bajtů byly zpracovány. V *wchar*uchováváte žádnou hodnotu , ale *mbstate* je aktualizován, aby se funkce restartovala.

## <a name="remarks"></a>Poznámky

Pokud *mbchar* je ukazatel null, funkce je ekvivalentní volání:

`mbrtowc(NULL, "", 1, &mbstate)`

V tomto případě jsou ignorovány hodnoty argumentů *wchar* a *count.*

Pokud *mbchar* není ukazatel null, funkce zkontroluje *počet* bajtů z *mbchar* určit požadovaný počet bajtů, které jsou nutné k dokončení další vícebajtový znak. Pokud je platný další znak, odpovídající vícebajtový znak je uložen v *wchar,* pokud není ukazatel null. Pokud je znak odpovídající široký znak null, výsledný stav *mbstate* je počáteční stav převodu.

Funkce **mbrtowc** se liší od [mbtowc, _mbtowc_l](mbtowc-mbtowc-l.md) svou restartovatelností. Stav převodu je uložen v *mbstate* pro následná volání stejné nebo jiné restartovatelné funkce. Výsledky nejsou definovány při míchání použití restartovatelných a nerestartovatelných funkcí.  Například aplikace by měla použít **wcsrlen** místo **wcslen,** pokud je použito následné volání **wcsrtombs** místo **wcstombs**.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

## <a name="example"></a>Příklad

Převede vícebajtový znak na jeho široký znak ekvivalent.

```cpp
// crt_mbrtowc.cpp

#include <stdio.h>
#include <mbctype.h>
#include <string.h>
#include <locale.h>
#include <wchar.h>

#define BUF_SIZE 100

int Sample(char* szIn, wchar_t* wcOut, int nMax)
{
    mbstate_t   state = {0}; // Initial state
    size_t      nConvResult,
                nmbLen = 0,
                nwcLen = 0;
    wchar_t*    wcCur = wcOut;
    wchar_t*    wcEnd = wcCur + nMax;
    const char* mbCur = szIn;
    const char* mbEnd = mbCur + strlen(mbCur) + 1;
    char*       szLocal;

    // Sets all locale to French_Canada.1252
    szLocal = setlocale(LC_ALL, "French_Canada.1252");
    if (!szLocal)
    {
        printf("The fuction setlocale(LC_ALL, \"French_Canada.1252\") failed!\n");
        return 1;
    }

    printf("Locale set to: \"%s\"\n", szLocal);

    // Sets the code page associated current locale's code page
    // from a previous call to setlocale.
    if (_setmbcp(_MB_CP_SBCS) == -1)
    {
        printf("The fuction _setmbcp(_MB_CP_SBCS) failed!");
        return 1;
    }

    while ((mbCur < mbEnd) && (wcCur < wcEnd))
    {
        //
        nConvResult = mbrtowc(wcCur, mbCur, 1, &state);
        switch (nConvResult)
        {
            case 0:
            {  // done
                printf("Conversion succeeded!\nMultibyte String: ");
                printf(szIn);
                printf("\nWC String: ");
                wprintf(wcOut);
                printf("\n");
                mbCur = mbEnd;
                break;
            }

            case -1:
            {  // encoding error
                printf("The call to mbrtowc has detected an encoding error.\n");
                mbCur = mbEnd;
                break;
            }

            case -2:
            {  // incomplete character
                if   (!mbsinit(&state))
                {
                    printf("Currently in middle of mb conversion, state = %x\n", state);
                    // state will contain data regarding lead byte of mb character
                }

                ++nmbLen;
                ++mbCur;
                break;
            }

            default:
            {
                if   (nConvResult > 2) // The multibyte should never be larger than 2
                {
                    printf("Error: The size of the converted multibyte is %d.\n", nConvResult);
                }

                ++nmbLen;
                ++nwcLen;
                ++wcCur;
                ++mbCur;
            break;
            }
        }
    }

   return 0;
}

int main(int argc, char* argv[])
{
    char    mbBuf[BUF_SIZE] = "AaBbCc\x9A\x8B\xE0\xEF\xF0xXyYzZ";
    wchar_t wcBuf[BUF_SIZE] = {L''};

    return Sample(mbBuf, wcBuf, BUF_SIZE);
}
```

### <a name="sample-output"></a>Vzorový výstup

```Output
Locale set to: "French_Canada.1252"
Conversion succeeded!
Multibyte String: AaBbCcÜïα∩≡xXyYzZ
WC String: AaBbCcÜïα∩≡xXyYzZ
```

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**mbrtowc**|\<wchar.h>|

## <a name="see-also"></a>Viz také

[Převod dat](../../c-runtime-library/data-conversion.md)<br/>
[Národní prostředí](../../c-runtime-library/locale.md)<br/>
[Výklad sekvencí vícebajtových znaků](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
