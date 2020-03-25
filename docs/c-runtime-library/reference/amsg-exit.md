---
title: _amsg_exit
ms.date: 11/04/2016
api_name:
- _amsg_exit
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
- _amsg_exit
helpviewer_keywords:
- _amsg_exit
ms.assetid: 146d4faf-d763-43a4-b264-12711196456b
ms.openlocfilehash: 31979a3181dc57644f1e6877277884e55cebf733
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80170930"
---
# <a name="_amsg_exit"></a>_amsg_exit

Vygeneruje zadanou chybovou zprávu za běhu a pak ukončí vaši aplikaci s kódem chyby 255.

## <a name="syntax"></a>Syntaxe

```cpp
void _amsg_exit ( int rterrnum );
```

### <a name="parameters"></a>Parametry

*rterrnum*<br/>
Identifikační číslo chybové zprávy modulu runtime definované systémem.

## <a name="remarks"></a>Poznámky

Tato funkce emituje chybovou zprávu modulu runtime do **stderr** pro konzolové aplikace nebo zobrazí zprávu v okně se zprávou pro aplikace systému Windows. V režimu ladění můžete před ukončením vyvolat ladicí program.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|_amsg_exit|internal.h|
