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
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _callnewh
helpviewer_keywords:
- _callnewh
ms.assetid: 4dcb73e9-6384-4d12-a973-a8807d4de7a8
ms.openlocfilehash: 3990d4b15c25cfd6c753c2b1d44c112971ff59af
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82918803"
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

|Hodnota|Popis|
|-----------|-----------------|
|0|Chyba: buď není nainstalována žádná nová obslužná rutina, nebo není žádná nová obslužná rutina aktivní.|
|1|Úspěch: Nová obslužná rutina je nainstalovaná a aktivní. Přidělení paměti lze opakovat.|

## <a name="exceptions"></a>Výjimky

Tato funkce vyvolá [bad_alloc](../../standard-library/bad-alloc-class.md) , pokud nelze nalézt *novou obslužnou rutinu* .

## <a name="remarks"></a>Poznámky

*Nová obslužná rutina* je volána, pokud [operátor New](../../cpp/new-operator-cpp.md) nepodaří úspěšně přidělit paměť. Nová obslužná rutina pak může iniciovat některé vhodné akce, jako je uvolnění paměti, aby bylo následné přidělení úspěšné.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Pokud ho chcete změnit, přečtěte si téma [globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|_callnewh|interní. h|

## <a name="see-also"></a>Viz také

[_set_new_handler](set-new-handler.md)<br/>
[_set_new_mode](set-new-mode.md)<br/>
