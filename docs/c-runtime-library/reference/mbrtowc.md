---
title: mbrtowc
ms.date: 11/04/2016
api_name:
- mbrtowc
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- mbrtowc
helpviewer_keywords:
- mbrtowc function
ms.assetid: a1e87fcc-6de0-4ca1-bf26-508d28490286
ms.openlocfilehash: b4c68ae8df9821d862b9f742d8a8ef7ace19c981
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70952430"
---
# <a name="mbrtowc"></a>mbrtowc

Převede vícebajtový znak v aktuálním národním prostředí do ekvivalentního širšího znaku s možností restartu uprostřed vícebajtového znaku.

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

*wchar*<br/>
Adresa dlouhého znaku pro příjem převedeného řetězce s velkým počtem znaků (typ **wchar_t**). Tato hodnota může být ukazatel s hodnotou null, pokud není vyžadován žádný znak návratu do širšího rozsahu.

*mbchar*<br/>
Adresa posloupnosti bajtů (vícebajtový znak).

*výpočtu*<br/>
Počet bajtů, které mají být zkontrolovány.

*mbstate*<br/>
Ukazatel na objekt stavu konverze. Pokud je tato hodnota ukazatel s hodnotou null, funkce používá statický vnitřní objekt stavu konverze. Vzhledem k tomu, že interní objekt **mbstate_t** není bezpečný pro přístup z více vláken, doporučujeme vždy předat vlastní argument *mbstate* .

## <a name="return-value"></a>Návratová hodnota

Jedna z následujících hodnot:

0 další *počet* nebo méně bajtů dokončí vícebajtový znak, který představuje znak null, který je uložen v *WCHAR*, pokud *WCHAR* není ukazatel s hodnotou null.

1 pro *počítání*, včetně dalšího *počtu* nebo méně bajtů, dokončí platný vícebajtový znak. Vrácená hodnota je počet bajtů, které dokončí vícebajtový znak. Ekvivalent pro velký znak je uložen v *WCHAR*, pokud *WCHAR* není ukazatel s hodnotou null.

(size_t) (-1) Došlo k chybě kódování. Další *počet* nebo méně bajtů nepřispívají k kompletnímu a platnému vícebajtovým znakům. V tomto případě je **errno** nastaven na EILSEQ a stav posunutí konverze v *mbstate* není specifikováno.

(size_t) (-2) Další *počet* bajtů přispívá k nekompletnímu, ale potenciálně platnému vícebajtovým znakem a všechny bajty *počtu* byly zpracovány. V *WCHAR*se neukládá žádná hodnota, ale *mbstate* se aktualizuje, aby se restartovala funkce.

## <a name="remarks"></a>Poznámky

Pokud je *mbchar* ukazatel s hodnotou null, funkce je ekvivalentní volání:

`mbrtowc(NULL, "", 1, &mbstate)`

V tomto případě se hodnota argumentů *WCHAR* a *Count* ignoruje.

Pokud *mbchar* není ukazatel s hodnotou null, funkce ověří počet bajtů z *mbchar* a určí požadovaný *počet bajtů,* které jsou nutné k dokončení dalšího vícebajtového znaku. Pokud je další znak platný, odpovídající vícebajtový znak je uložen v *WCHAR* , pokud se nejedná o ukazatel s hodnotou null. Pokud je znak odpovídajícím znakem null, je výsledný stav *mbstate* počátečním stavem převodu.

Funkce **mbrtowc** se od jejího spuštění liší od [mbtowc, _mbtowc_l](mbtowc-mbtowc-l.md) . Stav konverze je uložen v *mbstate* pro následné volání stejné nebo jiné možné funkce, které lze spustit. Výsledky nejsou definovány při kombinování použití opakovaných a nerestartů funkcí.  Například aplikace by měla používat **wcsrlen** namísto **wcslen** , pokud je místo **wcstombs**použito následné volání **wcsrtombs** .

## <a name="example"></a>Příklad

Převede vícebajtový znak na jeho ekvivalent pro nejrůznější znaky.

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

## <a name="see-also"></a>Viz také:

[Převod dat](../../c-runtime-library/data-conversion.md)<br/>
[Národní prostředí](../../c-runtime-library/locale.md)<br/>
[Výklad sekvencí vícebajtových znaků](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
