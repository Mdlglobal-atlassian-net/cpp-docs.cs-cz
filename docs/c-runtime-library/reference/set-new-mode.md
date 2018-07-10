---
title: _set_new_mode – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _set_new_mode
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
- set_new_mode
- _set_new_mode
dev_langs:
- C++
helpviewer_keywords:
- handler modes
- _set_new_mode function
- set_new_mode function
ms.assetid: 4d14039a-e54e-4689-8c70-74a4b9834768
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9b914e950fd94435768c355f327d3d48a653e0d5
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32407142"
---
# <a name="setnewmode"></a>_set_new_mode

Nastaví nový režim obslužné rutiny pro **malloc –**.

## <a name="syntax"></a>Syntaxe

```cpp
int _set_new_mode( int newhandlermode );
```

### <a name="parameters"></a>Parametry

*newhandlermode*<br/>
Nový režim obslužné rutiny pro **malloc**; platná hodnota je 0 nebo 1.

## <a name="return-value"></a>Návratová hodnota

Vrátí obslužnou rutinu předchozí sada režimu pro **malloc –**. Návratová hodnota 1 značí, že při selhání při přidělování paměti, **malloc** označovaly jako nové rutiny obslužná rutina; vrácená hodnota 0 značí, že ho nebyla. Pokud *newhandlermode* argument není rovno 0 nebo 1, vrátí hodnotu -1.

## <a name="remarks"></a>Poznámky

C++ **_set_new_mode –** funkce nastaví nový režim obslužné rutiny pro [malloc –](malloc.md). Nový režim obslužná rutina označuje, jestli při selhání, **malloc –** je volat nové rutiny obslužných rutin jako sady pomocí [_set_new_handler –](set-new-handler.md). Ve výchozím nastavení **malloc** nevyvolá nové rutiny ovladače při selhání při přidělování paměti. Toto výchozí chování můžete přepsat tak, aby, když **malloc –** nepodaří přidělit paměť, **malloc –** volání nové rutiny obslužná rutina ve stejné způsobem **nové** nemá operátor Když dojde k chybě ze stejného důvodu. Další informace najdete v tématu [nové](../../cpp/new-operator-cpp.md) a [odstranit](../../cpp/delete-operator-cpp.md) operátory *referenční příručka jazyka C++*. Chcete-li přepsat výchozí nastavení, zavolejte:

```cpp
_set_new_mode(1);
```

časná v aplikaci nebo odkaz s Newmode.obj (viz [možnosti odkazů](../../c-runtime-library/link-options.md)).

Tato funkce ověří jeho parametru. Pokud *newhandlermode* nic jiné než 0 nebo 1, funkce vyvolá obslužnou rutinu neplatný parametr, jako popsané v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud chcete pokračovat, je povoleno spuštění **_ *** set_new_mode –** vrátí hodnotu -1 a nastaví **errno** k **einval –**.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_set_new_mode**|\<New.h >|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také

[Přidělení paměti](../../c-runtime-library/memory-allocation.md)<br/>
[calloc](calloc.md)<br/>
[free](free.md)<br/>
[realloc](realloc.md)<br/>
[_query_new_handler](query-new-handler.md)<br/>
[_query_new_mode](query-new-mode.md)<br/>
