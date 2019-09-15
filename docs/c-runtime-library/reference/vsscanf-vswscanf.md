---
title: vsscanf, vswscanf
ms.date: 11/04/2016
api_name:
- vsscanf
- vswscanf
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _vstscanf
- vsscanf
- vswscanf
helpviewer_keywords:
- vswscanf function
- vsscanf function
ms.assetid: e96180f2-df46-423d-b4eb-0a49ab819bde
ms.openlocfilehash: 5dabe603c1cd0c95411fec87b9c0344f28c5c698
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70945103"
---
# <a name="vsscanf-vswscanf"></a>vsscanf, vswscanf

Přečte formátovaná data z řetězce. K dispozici jsou bezpečnější verze těchto funkcí; viz [vsscanf_s, vswscanf_s](vsscanf-s-vswscanf-s.md).

## <a name="syntax"></a>Syntaxe

```C
int vsscanf(
   const char *buffer,
   const char *format,
   va_list arglist
);
int vswscanf(
   const wchar_t *buffer,
   const wchar_t *format,
   va_list arglist
);
```

### <a name="parameters"></a>Parametry

*vyrovnávací paměti*<br/>
Uložená data

*format*<br/>
Řetězec řízení formátu Další informace najdete v tématu [formátování pole Specifikace: scanf a wscanf Functions](../../c-runtime-library/format-specification-fields-scanf-and-wscanf-functions.md).

*arglist*<br/>
Seznam argumentů proměnných

## <a name="return-value"></a>Návratová hodnota

Každá z těchto funkcí vrátí počet polí, která jsou úspěšně převedena a přiřazena; Vrácená hodnota nezahrnuje pole, která byla načtena, ale nebyla přiřazena. Návratová hodnota 0 značí, že nebyla přiřazena žádná pole. Návratová hodnota je znak **EOF** pro chybu, nebo pokud je dosaženo konce řetězce před prvním převodem.

Pokud je *vyrovnávací paměť* nebo *Formát* ukazatel s **hodnotou null** , je vyvolána obslužná rutina neplatného parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, vrátí tyto funkce hodnotu-1 a nastaví **errno** na **EINVAL**.

Informace o těchto a dalších chybových kódech naleznete v tématu [errno, _doserrno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Poznámky

Funkce **vsscanf** čte data z *vyrovnávací paměti* do umístění, která jsou uvedena v každém argumentu v seznamu argumentů *Arglist* . Každý argument v seznamu musí být ukazatel na proměnnou, která má typ, který odpovídá specifikátoru typu ve *formátu*. Argument *Format* řídí interpretaci vstupních polí a má stejnou formu a funkci jako argument *Format* pro funkci **scanf** . Pokud se provádí kopírování mezi řetězci, které se překrývají, chování není definováno.

> [!IMPORTANT]
> Při použití **vsscanf** ke čtení řetězce vždy zadejte šířku pro formát **% s** (například **"% 32S"** místo **"% s"** ); jinak nesprávně formátovaný vstup může způsobit přetečení vyrovnávací paměti.

**vswscanf** je **vsscanf**verze s velkým znakem; argumenty **vswscanf** jsou řetězce s libovolným znakem. **vsscanf** nezpracovává vícebajtové šestnáctkové znaky. **vswscanf** nezpracovává šestnáctkové znaky Unicode s plnou šířkou nebo "zónu kompatibility". V opačném případě se **vswscanf** a **vsscanf** chovají stejně.

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_vstscanf**|**vsscanf**|**vsscanf**|**vswscanf**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**vsscanf**|\<stdio.h>|
|**vswscanf**|\<stdio. h > nebo \<WCHAR. h >|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_vsscanf.c
// compile with: /W3
// This program uses vsscanf to read data items
// from a string named tokenstring, then displays them.

#include <stdio.h>
#include <stdarg.h>

int call_vsscanf(char *tokenstring, char *format, ...)
{
    int result;
    va_list arglist;
    va_start(arglist, format);
    result = vsscanf(tokenstring, format, arglist);
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
    call_vsscanf(tokenstring, "%80s", s);
    call_vsscanf(tokenstring, "%c", &c);
    call_vsscanf(tokenstring, "%d", &i);
    call_vsscanf(tokenstring, "%f", &fp);

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

[Vstup/výstup datového proudu](../../c-runtime-library/stream-i-o.md)<br/>
[scanf, _scanf_l, wscanf, _wscanf_l](scanf-scanf-l-wscanf-wscanf-l.md)<br/>
[sscanf, _sscanf_l, swscanf, _swscanf_l](sscanf-sscanf-l-swscanf-swscanf-l.md)<br/>
[sprintf, _sprintf_l, swprintf, _swprintf_l, \__swprintf_l](sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)<br/>
[vsscanf_s, vswscanf_s](vsscanf-s-vswscanf-s.md)<br/>
