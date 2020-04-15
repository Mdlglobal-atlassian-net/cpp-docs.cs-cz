---
title: _callnewh
ms.date: 4/2/2020
api_name:
- _callnewh
- _o__callnewh
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
- api-ms-win-crt-heap-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _callnewh
helpviewer_keywords:
- _callnewh
ms.assetid: 4dcb73e9-6384-4d12-a973-a8807d4de7a8
ms.openlocfilehash: d93de7f963a370810ed3b30af04d6d602abf6313
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81333663"
---
# <a name="_callnewh"></a>_callnewh

Volá aktuálně nainstalovanou *novou obslužnou rutinu*.

## <a name="syntax"></a>Syntaxe

```cpp
int _callnewh(
   size_t size
   )
```

### <a name="parameters"></a>Parametry

*Velikost*<br/>
Množství paměti, které se [nový operátor](../../cpp/new-operator-cpp.md) pokusil přidělit.

## <a name="return-value"></a>Návratová hodnota

|Hodnota|Popis|
|-----------|-----------------|
|0|Selhání: Buď není nainstalována žádná nová obslužná rutina nebo je aktivní žádná nová obslužná rutina.|
|1|Úspěch: Nová obslužná rutina je nainstalována a aktivní. Přidělení paměti lze opakovat.|

## <a name="exceptions"></a>Výjimky

Tato funkce vyvolá [bad_alloc](../../standard-library/bad-alloc-class.md) pokud nelze nalézt *novou obslužnou rutinu.*

## <a name="remarks"></a>Poznámky

*Nová obslužná rutina* je volána, pokud [se novému operátoru](../../cpp/new-operator-cpp.md) nepodaří úspěšně přidělit paměť. Nová obslužná rutina pak může zahájit některé vhodné akce, jako je například uvolnění paměti tak, aby následné přidělení úspěšné.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|_callnewh|internal.h|

## <a name="see-also"></a>Viz také

[_set_new_handler](set-new-handler.md)<br/>
[_set_new_mode](set-new-mode.md)<br/>
