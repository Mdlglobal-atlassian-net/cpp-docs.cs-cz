---
title: _tempnam, _wtempnam, tmpnam, _wtmpnam
ms.date: 11/04/2016
api_name:
- _wtempnam
- _wtmpnam
- tmpnam
- _tempnam
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
- api-ms-win-crt-stdio-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- wtempnam
- _wtmpnam
- wtmpnam
- tmpnam
- _wtempnam
- _tempnam
helpviewer_keywords:
- wtempnam function
- file names [C++], creating temporary
- _tempnam function
- ttmpnam function
- tmpnam function
- tempnam function
- wtmpnam function
- temporary files, creating
- file names [C++], temporary
- _ttmpnam function
- _wtmpnam function
- _wtempnam function
ms.assetid: 3ce75f0f-5e30-42a6-9791-8d7cbfe70fca
ms.openlocfilehash: 9fd1eb9f2f718afec5b7d5555145fcd7e5cc17cf
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70957523"
---
# <a name="_tempnam-_wtempnam-tmpnam-_wtmpnam"></a>_tempnam, _wtempnam, tmpnam, _wtmpnam

Vygenerujte názvy, které můžete použít k vytvoření dočasných souborů. K dispozici jsou bezpečnější verze některých z těchto funkcí; viz [tmpnam_s, _wtmpnam_s](tmpnam-s-wtmpnam-s.md).

## <a name="syntax"></a>Syntaxe

```C
char *_tempnam(
   const char *dir,
   const char *prefix
);
wchar_t *_wtempnam(
   const wchar_t *dir,
   const wchar_t *prefix
);
char *tmpnam(
   char *str
);
wchar_t *_wtmpnam(
   wchar_t *str
);
```

### <a name="parameters"></a>Parametry

*prefix*<br/>
Řetězec, který bude označené jako nedokončené do názvů vrácených pomocí **_tempnam**.

*dir*<br/>
Cesta použitá v názvu souboru, pokud neexistuje žádná proměnná prostředí TMP, nebo pokud TMP není platný adresář.

*str*<br/>
Ukazatel, který bude obsahovat vygenerovaný název a bude shodný s názvem vráceným funkcí. Toto je pohodlný způsob, jak uložit vygenerovaný název.

## <a name="return-value"></a>Návratová hodnota

Každá z těchto funkcí vrací ukazatel na název generovaný nebo **null** , pokud dojde k chybě. K selhání může dojít, pokud se pokusíte o více než **TMP_MAX** (viz stdio. H) volání s **tmpnam** nebo pokud používáte **_tempnam** a v proměnné prostředí TMP a v parametru *dir* je zadán neplatný název adresáře.

> [!NOTE]
> Ukazatele vracené **tmpnam** a **_wtmpnam** Point do vnitřních statických vyrovnávacích pamětí. pro zrušení přidělení těchto ukazatelů by neměl být volána metoda [Free](free.md) . k ukazatelům přiděleným **_tempnam** a **_wtempnam**se musí volat **bezplatné** požadavky.

## <a name="remarks"></a>Poznámky

Každá z těchto funkcí vrací název souboru, který aktuálně neexistuje. **tmpnam** vrátí název, který je jedinečný v určeném dočasném adresáři Windows vráceném funkcí [GetTempPathW](/windows/win32/api/fileapi/nf-fileapi-gettemppathw). tempnam vygeneruje jedinečný název v jiném než určeném adresáři.  **\_** Všimněte si, že pokud je název souboru před označené jako nedokončené zpětným lomítkem a žádné informace o cestě, jako je například \fname21, znamená to, že název je platný pro aktuální pracovní adresář.

V případě **tmpnam**můžete tento vygenerovaný název souboru Uložit do *str*. Pokud má str **hodnotu null**, výsledek **tmpnam** ponechá interní statickou vyrovnávací paměť. Proto jakákoli následná volání zničí tuto hodnotu. Název generovaný pomocí **tmpnam** se skládá z programu generovaného programem a po prvním volání **tmpnam**je přípona souboru sekvenčních čísel v základní 32 (. 1 –. VVU, když **TMP_MAX** v stdio. H je 32 767).

**_tempnam** vygeneruje jedinečný název souboru pro adresář vybraný pomocí následujících pravidel:

- Pokud je proměnná prostředí TMP definovaná a nastavená na platný název adresáře, vygenerují se jedinečné názvy souborů pro adresář určený pomocí TMP.

- Pokud proměnná prostředí TMP není definovaná nebo pokud je nastavená na název adresáře, který neexistuje, **_tempnam** použije parametr *dir* jako cestu, pro kterou bude generovat jedinečné názvy.

- Pokud proměnná prostředí TMP není definovaná nebo pokud je nastavená na název adresáře, který neexistuje, a *Pokud je adresář* buď **null** , nebo nastavený na název adresáře, který neexistuje, **_tempnam** použije aktuální pracovní adresář pro genové zpracování. vyhodnotí jedinečné názvy. Pokud v současné době TMP i *dir* určují názvy adresářů, které neexistují, volání funkce **_tempnam** se nezdaří.

Název vrácený funkcí **_tempnam** bude zřetězením *předpony* a sekvenčního čísla, které se spojí a vytvoří jedinečný název souboru pro zadaný adresář. **_tempnam** vygeneruje názvy souborů bez přípony. **_tempnam** používá [k přidělení prostoru pro název](malloc.md) souboru. program zodpovídá za uvolnění tohoto místa, pokud už ho nepotřebujete.

**_tempnam** a **tmpnam** automaticky zpracovávají řetězcové argumenty vícebajtových znaků podle potřeby a zjišťují sekvence vícebajtových znaků podle znakové stránky OEM získané z operačního systému. **_wtempnam** je **_tempnam**verze s velkým znakem; argumenty a návratová hodnota **_wtempnam** jsou řetězce s velkým počtem znaků. **_wtempnam** a **_tempnam** se chovají stejně, s výjimkou toho, že **_wtempnam** zpracovává řetězce vícebajtových znaků. **_wtmpnam** je **tmpnam**verze s velkým znakem; argument a návratová hodnota **_wtmpnam** jsou řetězce s velkým počtem znaků. **_wtmpnam** a **tmpnam** se chovají stejně, s výjimkou toho, že **_wtmpnam** zpracovává řetězce vícebajtových znaků.

Pokud jsou definovány **_DEBUG** a **_CRTDBG_MAP_ALLOC** , jsou **_tempnam** a **_wtempnam** nahrazeny voláními [_tempnam_dbg a _wtempnam_dbg](tempnam-dbg-wtempnam-dbg.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_ttmpnam**|**tmpnam**|**tmpnam**|**_wtmpnam**|
|**_ttempnam**|**_tempnam**|**_tempnam**|**_wtempnam**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_tempnam**|\<stdio.h>|
|**_wtempnam**, **_wtmpnam**|\<stdio. h > nebo \<WCHAR. h >|
|**tmpnam**|\<stdio.h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_tempnam.c
// compile with: /W3
// This program uses tmpnam to create a unique filename in the
// temporary directory, and _tempname to create a unique filename
// in C:\\tmp.

#include <stdio.h>
#include <stdlib.h>

int main(void)
{
   char * name1 = NULL;
   char * name2 = NULL;
   char * name3 = NULL;

   // Create a temporary filename for the current working directory:
   if ((name1 = tmpnam(NULL)) != NULL) { // C4996
   // Note: tmpnam is deprecated; consider using tmpnam_s instead
      printf("%s is safe to use as a temporary file.\n", name1);
   } else {
      printf("Cannot create a unique filename\n");
   }

   // Create a temporary filename in temporary directory with the
   // prefix "stq". The actual destination directory may vary
   // depending on the state of the TMP environment variable and
   // the global variable P_tmpdir.

   if ((name2 = _tempnam("c:\\tmp", "stq")) != NULL) {
      printf("%s is safe to use as a temporary file.\n", name2);
   } else {
      printf("Cannot create a unique filename\n");
   }

   // When name2 is no longer needed:
   if (name2) {
      free(name2);
   }

   // Unset TMP environment variable, then create a temporary filename in C:\tmp.
   if (_putenv("TMP=") != 0) {
      printf("Could not remove TMP environment variable.\n");
   }

   // With TMP unset, we will use C:\tmp as the temporary directory.
   // Create a temporary filename in C:\tmp with prefix "stq".
   if ((name3 = _tempnam("c:\\tmp", "stq")) != NULL) {
      printf("%s is safe to use as a temporary file.\n", name3);
   }
   else {
      printf("Cannot create a unique filename\n");
   }

   // When name3 is no longer needed:
   if (name3) {
      free(name3);
   }

   return 0;
}
```

```Output
C:\Users\LocalUser\AppData\Local\Temp\sriw.0 is safe to use as a temporary file.
C:\Users\LocalUser\AppData\Local\Temp\stq2 is safe to use as a temporary file.
c:\tmp\stq3 is safe to use as a temporary file.
```

## <a name="see-also"></a>Viz také:

[Vstup/výstup datového proudu](../../c-runtime-library/stream-i-o.md)<br/>
[_getmbcp](getmbcp.md)<br/>
[malloc](malloc.md)<br/>
[_setmbcp](setmbcp.md)<br/>
[tmpfile](tmpfile.md)<br/>
[tmpfile_s](tmpfile-s.md)<br/>
