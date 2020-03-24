---
title: fwide
ms.date: 11/04/2016
api_name:
- fwide
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
- fwide
helpviewer_keywords:
- fwide function
ms.assetid: a4641f5b-d74f-4946-95d5-53a64610d28d
ms.openlocfilehash: 652aee03bfb5504a51d74efb326cc7a3d7c28649
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80171200"
---
# <a name="fwide"></a>fwide

Neimplementované.

## <a name="syntax"></a>Syntaxe

```C
int fwide(
   FILE *stream,
   int mode;
);
```

### <a name="parameters"></a>Parametry

*Stream*<br/>
Ukazatel na strukturu **souborů** (ignorováno).

*Mode*<br/>
Nová šířka datového proudu: kladná hodnota pro velký znak, záporná pro bajt, nula, která nezůstane beze změny. (Tato hodnota se ignoruje.)

## <a name="return-value"></a>Návratová hodnota

Tato funkce aktuálně vrací jenom *režim*.

## <a name="remarks"></a>Poznámky

Aktuální verze této funkce nedodržuje Standard.

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaný hlavičkový soubor|
|--------------|---------------------|
|**fwide**|\<WCHAR. h >|

Další informace najdete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).
