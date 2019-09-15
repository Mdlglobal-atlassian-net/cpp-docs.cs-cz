---
title: _callnewh
ms.date: 11/04/2016
api_name:
- _callnewh
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _callnewh
helpviewer_keywords:
- _callnewh
ms.assetid: 4dcb73e9-6384-4d12-a973-a8807d4de7a8
ms.openlocfilehash: 3e14450538807b164897c335f7e37d82d8562314
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70939384"
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

*hodnota*<br/>
Velikost paměti, kterou byl [Nový operátor](../../cpp/new-operator-cpp.md) proveden při pokusu o přidělení.

## <a name="return-value"></a>Návratová hodnota

|Value|Popis|
|-----------|-----------------|
|0|Poruše Buď není nainstalována žádná nová obslužná rutina, nebo není žádná nová obslužná rutina aktivní.|
|1|Nástup Nová obslužná rutina je nainstalována a aktivní. Přidělení paměti lze opakovat.|

## <a name="exceptions"></a>Výjimky

Tato funkce vyvolá [bad_alloc](../../standard-library/bad-alloc-class.md) , pokud nelze najít *novou obslužnou rutinu* .

## <a name="remarks"></a>Poznámky

*Nová obslužná rutina* je volána, pokud [operátor New](../../cpp/new-operator-cpp.md) nepodaří úspěšně přidělit paměť. Nová obslužná rutina pak může iniciovat některé vhodné akce, jako je uvolnění paměti, aby bylo následné přidělení úspěšné.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|_callnewh|internal.h|

## <a name="see-also"></a>Viz také:

[_set_new_handler](set-new-handler.md)<br/>
[_set_new_mode](set-new-mode.md)<br/>
