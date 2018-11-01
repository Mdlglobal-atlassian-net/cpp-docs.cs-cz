---
title: mbrtowc
ms.date: 11/04/2016
apiname:
- mbrtowc
apilocation:
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
apitype: DLLExport
f1_keywords:
- mbrtowc
helpviewer_keywords:
- mbrtowc function
ms.assetid: a1e87fcc-6de0-4ca1-bf26-508d28490286
ms.openlocfilehash: bd719e7b336333f6e06a1db9b1e34784575a1602
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50581828"
---
# <a name="mbrtowc"></a>mbrtowc

Převeďte vícebajtového znaku v aktuálním národním prostředí ekvivalentní širokého znaku pomocí funkce restartování uprostřed vícebajtového znaku.

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
Adresa široký znak, široký znak převedený řetězec (typ **wchar_t**). Tato hodnota může být ukazatel s hodnotou null, pokud žádný návratový širokého znaku je povinný.

*mbchar*<br/>
Adresa sekvence bajtů (vícebajtového znaku).

*Počet*<br/>
Počet bajtů ke kontrole.

*mbstate*<br/>
Ukazatel na objekt převod stavu. Pokud tato hodnota je ukazatel s hodnotou null, funkce používá interní statického převodu stav objektu. Protože vnitřní **mbstate_t** objektu není bezpečná pro vlákno, doporučujeme vám vždy předání vlastní *mbstate* argument.

## <a name="return-value"></a>Návratová hodnota

Jeden z následujících hodnot:

0 na další *počet* nebo menší počet bajtů dokončení vícebajtového znaku, který představuje hodnotu null široký znak, který je uložený v *wchar*, pokud *wchar* není ukazatel s hodnotou null.

1 *počet*, včetně následujících *počet* nebo menší počet bajtů je platný vícebajtový znak. Vrácená hodnota je počet bajtů, které dokončení vícebajtového znaku. Široký znak, který je ekvivalentní je uložen v *wchar*, pokud *wchar* není ukazatel s hodnotou null.

(size_t) (-1) Došlo k chybě kódování. Další *počet* nebo menší počet bajtů se nepodílejí na dokončení a je platný vícebajtový znak. V takovém případě **errno** je nastavena na EILSEQ a stav převodu shift v *mbstate* není zadána.

(size_t) -(2) Další *počet* bajtů přispívat k neúplný, ale potenciálně platný vícebajtový znak a ke všem *počet* byly zpracovány bajtů. Žádná hodnota je uložená v *wchar*, ale *mbstate* se aktualizuje a restartuje funkce.

## <a name="remarks"></a>Poznámky

Pokud *mbchar* je ukazatel s hodnotou null, je ekvivalentní volání funkce:

`mbrtowc(NULL, "", 1, &mbstate)`

V takovém případě hodnotu argumentů *wchar* a *počet* jsou ignorovány.

Pokud *mbchar* není ukazatel s hodnotou null, funkce zkontroluje *počet* bajtů z *mbchar* určit požadovaný počet bajtů, které jsou vyžadovány k dokončení následujících vícebajtový znak. Pokud následující znak je platný, odpovídající vícebajtový znak je uložen v *wchar* Pokud není ukazatel s hodnotou null. Pokud je znak odpovídající široký null znaků, výsledný stav *mbstate* je počáteční převod stavu.

**Mbrtowc –** funkce se liší od [mbtowc _mbtowc_l –](mbtowc-mbtowc-l.md) podle jeho restartability. Stav převodu je uložen v *mbstate* pro pozdější volání na stejné nebo jiné funkce nabízet možnost restartování. Při použití funkcí restartovatelnou službu a nonrestartable případě nejsou výsledky definovány.  Například by měla aplikace použít **wcsrlen** místo **wcslen –** Pokud následných volání **wcsrtombs –** se použije namísto **wcstombs –**.

## <a name="example"></a>Příklad

Převede vícebajtového znaku na jeho ekvivalentní širokého znaku.

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
