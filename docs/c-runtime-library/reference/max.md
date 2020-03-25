---
title: __max
ms.date: 04/05/2018
api_name:
- __max
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
- max
- __max
helpviewer_keywords:
- max macro
- maximum macro
- __max macro
ms.assetid: 05c936f6-0e22-45d6-a58d-4bc102e9dae2
ms.openlocfilehash: 4cdfd99ec344cd357900d76dfc7f9400046e448a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80170186"
---
# <a name="__max"></a>__max

Makro preprocesoru, které vrací větší ze dvou hodnot.

## <a name="syntax"></a>Syntaxe

```C
#define __max(a,b) (((a) > (b)) ? (a) : (b))
```

### <a name="parameters"></a>Parametry

*a*, *b*<br/>
Hodnoty libovolného číselného typu, které mají být porovnány.

## <a name="return-value"></a>Návratová hodnota

**__max** vrátí větší z jeho argumentů.

## <a name="remarks"></a>Poznámky

Makro **__max** porovná dvě hodnoty a vrátí hodnotu větší. Argumenty mohou být libovolného číselného datového typu, podepsán nebo bez znaménka. Oba argumenty i návratová hodnota musí být stejného datového typu.

Vrácený argument je vyhodnocen dvakrát makrem. To může vést k neočekávaným výsledkům, pokud je argument výraz, který při vyhodnocení změní jeho hodnotu, například `*p++`.

## <a name="requirements"></a>Požadavky

|– Makro|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**__max**|\<Stdlib. h >|

## <a name="example"></a>Příklad

Další informace najdete v příkladu pro [__min](min.md).

## <a name="see-also"></a>Viz také

[Podpora plovoucí desetinné čárky](../../c-runtime-library/floating-point-support.md)<br/>
[__min](min.md)<br/>
