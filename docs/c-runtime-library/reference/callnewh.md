---
title: _callnewh
ms.date: 11/04/2016
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
helpviewer_keywords:
- _callnewh
ms.assetid: 4dcb73e9-6384-4d12-a973-a8807d4de7a8
ms.openlocfilehash: 98526f6c8c40b71104345563db71ef098b6cfb8d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50643661"
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
Množství paměti, která [operátor new](../../cpp/new-operator-cpp.md) pokusil přidělit.

## <a name="return-value"></a>Návratová hodnota

|Hodnota|Popis|
|-----------|-----------------|
|0|Chyba: Je nainstalován buď žádné novou obslužnou rutinu nebo není aktivní žádná novou obslužnou rutinu.|
|1|Úspěch: Novou obslužnou rutinu je nainstalovaný a aktivní. Přidělení paměti lze opakovat.|

## <a name="exceptions"></a>Výjimky

Tato funkce vyvolá [bad_alloc –](../../standard-library/bad-alloc-class.md) Pokud *novou obslužnou rutinu* nejde najít.

## <a name="remarks"></a>Poznámky

*Novou obslužnou rutinu* je volána, pokud [operátor new](../../cpp/new-operator-cpp.md) úspěšně přidělení paměti se nezdaří. Nová obslužná rutina může být potom iniciovat některé příslušnou akci, jako je například uvolnění paměti tak, aby úspěšné následné přidělení.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|_callnewh|internal.h|

## <a name="see-also"></a>Viz také:

[_set_new_handler](set-new-handler.md)<br/>
[_set_new_mode](set-new-mode.md)<br/>
