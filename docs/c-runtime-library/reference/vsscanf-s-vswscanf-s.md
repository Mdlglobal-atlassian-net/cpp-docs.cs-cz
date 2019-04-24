---
title: vsscanf_s, vswscanf_s
ms.date: 11/04/2016
apiname:
- vswscanf_s
- vsscanf_s
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
apitype: DLLExport
f1_keywords:
- vsscanf_s
- vswscanf_s
- _vstscanf_s
ms.assetid: 7b732e68-c6f4-4579-8917-122f5a7876e1
ms.openlocfilehash: 3106e3533f5bb65334f8a4f3d38f55d886faef4c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62188709"
---
# <a name="vsscanfs-vswscanfs"></a>vsscanf_s, vswscanf_s

Čtení formátovaných dat z řetězce. Tyto verze [vsscanf – vswscanf –](vsscanf-vswscanf.md) mají rozšíření zabezpečení popsaná v [funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Syntaxe

```C
int vsscanf_s(
   const char *buffer,
   const char *format,
   va_list argptr
);
int vswscanf_s(
   const wchar_t *buffer,
   const wchar_t *format,
   va_list arglist
);
```

### <a name="parameters"></a>Parametry

*Vyrovnávací paměti*<br/>
Uložená data

*Formát*<br/>
Řetězec řízení formátu Další informace najdete v tématu [pole Specifikace formátu: funkce scanf a wscanf](../../c-runtime-library/format-specification-fields-scanf-and-wscanf-functions.md).

*arglist*<br/>
Seznam argumentů s proměnnou délkou.

## <a name="return-value"></a>Návratová hodnota

Každá z těchto funkcí vrátí počet polí, která jsou úspěšně převedena a přidělena; Vrácená hodnota nezahrnuje pole, která byla načtena, ale nejsou přiřazena. Vrácená hodnota 0 označuje, že nebyla přiřazena žádná pole. Vrácená hodnota je **EOF** pro chybu nebo pokud je dosaženo konce řetězce před prvním převodem.

Pokud *vyrovnávací paměti* nebo *formátu* je **NULL** vyvolána ukazatel, obslužná rutina neplatného parametru, jak je popsáno v [Parameter Validation](../../c-runtime-library/parameter-validation.md). Pokud smí provádění pokračovat, vrátí funkce hodnotu -1 a nastaví **errno** k **EINVAL**.

Informace o těchto a dalších chybových kódech naleznete v tématu [errno _doserrno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Poznámky

**Vsscanf_s** funkce načítá data z *vyrovnávací paměti* do umístění, která jsou uvedena v každém argumentu v *seznam_argumentů* seznam argumentů. Argumenty v seznamu argumentů určují odkazy na proměnné, které mají typ, který odpovídá specifikátoru typů ve *formátu*. Na rozdíl od méně bezpečné verze **vsscanf –**, parametr velikosti vyrovnávací paměti je povinný, pokud používáte znaky pole typu **c**, **C**, **s**, **S**, nebo sad řízení řetězců, které jsou uzavřeny v **[]**. Velikost vyrovnávací paměti ve znacích musí být dodána jako další parametr ihned po každého parametru mezipaměti, který jej vyžaduje.

Vyrovnávací paměť obsahuje ukončující znak null. Pole pro specifikaci šířky slouží k zajištění, že token, který je určen pro čtení, se vejde do vyrovnávací paměti. Pokud žádná pole pro specifikaci šířky a čtený token je nevejdou do vyrovnávací paměti, není nic zapsáno do vyrovnávací paměti.

Další informace najdete v tématu [scanf_s _scanf_s_l –, wscanf_s – _wscanf_s_l –](scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md) a [scanf – znaky pole typu](../../c-runtime-library/scanf-type-field-characters.md).

> [!NOTE]
> Velikost parametru je typu **bez znaménka**, nikoli **size_t**.

*Formátu* argument řídí interpretaci vstupních polí a má stejnou formu a funkci jako *formátu* argument **scanf_s** funkce. Pokud ke kopírování dojde mezi řetězci, které se překrývají, chování není definováno.

**vswscanf_s** je verze širokého znaku **vsscanf_s**; argumenty, které mají **vswscanf_s** jsou širokoznaké řetězce. **vsscanf_s** nezpracovává vícebajtové znaky v šestnáctkové soustavě. **vswscanf_s** nezpracovává šestnáctkové kódování Unicode s plnou šířkou nebo znaky "oblasti kompatibility". V opačném případě **vswscanf_s** a **vsscanf_s** chovají identicky.

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE a _MBCS nejsou definovány|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_vstscanf_s**|**vsscanf_s**|**vsscanf_s**|**vswscanf_s**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**vsscanf_s**|\<stdio.h>|
|**vswscanf_s**|\<stdio.h > nebo \<wchar.h >|

Další informace o kompatibilitě, naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_vsscanf_s.c
// compile with: /W3
// This program uses vsscanf_s to read data items
// from a string named tokenstring, then displays them.

#include <stdio.h>
#include <stdarg.h>
#include <stdlib.h>

int call_vsscanf_s(char *tokenstring, char *format, ...)
{
    int result;
    va_list arglist;
    va_start(arglist, format);
    result = vsscanf_s(tokenstring, format, arglist);
    va_end(arglist);
    return result;
}

int main( void )
{
    char  tokenstring[] = "15 12 14...";
    char  s[81];
    char  c;
    int   i;
    float fp;

    // Input various data from tokenstring:
    // max 80 character string:
    call_vsscanf_s(tokenstring, "%80s", s, _countof(s));
    call_vsscanf_s(tokenstring, "%c", &c, sizeof(char));
    call_vsscanf_s(tokenstring, "%d", &i);
    call_vsscanf_s(tokenstring, "%f", &fp);

    // Output the data read
    printf("String    = %s\n", s);
    printf("Character = %c\n", c);
    printf("Integer:  = %d\n", i);
    printf("Real:     = %f\n", fp);
}
```

```Output
String    = 15
Character = 1
Integer:  = 15
Real:     = 15.000000
```

## <a name="see-also"></a>Viz také:

[Stream vstupně-výstupních operací](../../c-runtime-library/stream-i-o.md)<br/>
[scanf, _scanf_l, wscanf, _wscanf_l](scanf-scanf-l-wscanf-wscanf-l.md)<br/>
[sscanf, _sscanf_l, swscanf, _swscanf_l](sscanf-sscanf-l-swscanf-swscanf-l.md)<br/>
[sscanf_s, _sscanf_s_l, swscanf_s, _swscanf_s_l](sscanf-s-sscanf-s-l-swscanf-s-swscanf-s-l.md)<br/>
[sprintf, _sprintf_l, swprintf, _swprintf_l, \__swprintf_l](sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)<br/>
[vsscanf, vswscanf](vsscanf-vswscanf.md)<br/>
