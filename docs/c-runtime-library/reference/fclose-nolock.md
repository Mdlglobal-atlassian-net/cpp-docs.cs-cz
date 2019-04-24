---
title: _fclose_nolock
ms.date: 11/04/2016
apiname:
- _fclose_nolock
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
- api-ms-win-crt-stdio-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- fclose_nolock
- _fclose_nolock
helpviewer_keywords:
- streams, closing
- fclose_nolock function
- _fclose_nolock function
ms.assetid: b4af4392-5fc8-49bb-9fe2-ca7293d3ce04
ms.openlocfilehash: 440582bb42a1795721eab17b24be3e0bc3daf80f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62334967"
---
# <a name="fclosenolock"></a>_fclose_nolock

Zavře datového proudu bez zamčení vlákna.

## <a name="syntax"></a>Syntaxe

```C
int _fclose_nolock(
   FILE *stream
);
```

### <a name="parameters"></a>Parametry

*stream*<br/>
Ukazatel **souboru** struktury.

## <a name="return-value"></a>Návratová hodnota

**fclose –** vrátí hodnotu 0, pokud datový proud je uzavřen úspěšně. Vrátí **EOF** udávající chybu.

## <a name="remarks"></a>Poznámky

Tato funkce je nezamykací verze **fclose –**. Je identická s tím rozdílem, že nejsou chráněny před rušením jinými vlákny. Může být rychlejší, protože narůstání režii uzamykáním ostatních vláken. Tuto funkci lze používejte pouze v kontextech bezpečných na vlákna, jako je například aplikace s jedním vláknem nebo pokud volající obor již zpracovává izolaci vláken.

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaný hlavičkový soubor|
|--------------|---------------------|
|**_fclose_nolock**|\<stdio.h>|

Další informace o kompatibilitě naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[Stream vstupně-výstupních operací](../../c-runtime-library/stream-i-o.md)<br/>
[_close](close.md)<br/>
[_fdopen, _wfdopen](fdopen-wfdopen.md)<br/>
[fflush](fflush.md)<br/>
[fopen, _wfopen](fopen-wfopen.md)<br/>
[freopen, _wfreopen](freopen-wfreopen.md)<br/>
