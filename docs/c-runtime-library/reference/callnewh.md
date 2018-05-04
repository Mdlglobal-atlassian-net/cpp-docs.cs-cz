---
title: _callnewh | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _callnewh
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
- api-ms-win-crt-heap-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _callnewh
dev_langs:
- C++
helpviewer_keywords:
- _callnewh
ms.assetid: 4dcb73e9-6384-4d12-a973-a8807d4de7a8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a40d8f621b7098618b9be3872620d5294013fbe3
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="callnewh"></a>_callnewh

Volá aktuálně nainstalované *novou obslužnou rutinu*.

## <a name="syntax"></a>Syntaxe

```cpp
int _callnewh(
   size_t size
   )
```

### <a name="parameters"></a>Parametry

*Velikost*<br/>
Velikost paměti, který [operátor new](../../cpp/new-operator-cpp.md) pokusil přidělit.

## <a name="return-value"></a>Návratová hodnota

|Hodnota|Popis|
|-----------|-----------------|
|0|Chyba: Žádné nové rutiny se nainstaluje nebo žádné nové obslužná rutina je aktivní.|
|1|Úspěch: Novou obslužnou rutinu je nainstalována a aktivní. Přidělení paměti můžete opakovat.|

## <a name="exceptions"></a>Výjimky

Tato funkce vyvolá [bad_alloc](../../standard-library/bad-alloc-class.md) Pokud *novou obslužnou rutinu* nebyl nalezen.

## <a name="remarks"></a>Poznámky

*Novou obslužnou rutinu* je volána, pokud [operátor new](../../cpp/new-operator-cpp.md) nepodaří úspěšně přidělit paměť. Nové obslužná rutina může potom zahájit některé příslušné akce, jako je například uvolnění paměti, aby být úspěšné následné přidělení.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|_callnewh|internal.h|

## <a name="see-also"></a>Viz také

[_set_new_handler](set-new-handler.md)<br/>
[_set_new_mode](set-new-mode.md)<br/>
