---
title: _recalloc_dbg – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _recalloc_dbg
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
apitype: DLLExport
f1_keywords:
- recalloc_dbg
- _recalloc_dbg
dev_langs:
- C++
helpviewer_keywords:
- _recalloc_dbg function
- recalloc_dbg function
ms.assetid: 43c3e9b2-be6d-4508-9b0f-3220c8a47ca3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3de6adddc4e7d95f3212c80666816d4855897388
ms.sourcegitcommit: 6e3cf8df676d59119ce88bf5321d063cf479108c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/22/2018
ms.locfileid: "34451046"
---
# <a name="recallocdbg"></a>_recalloc_dbg

Přidělí pole a inicializuje jeho prvky na hodnotu 0 (pouze ladicí verze).

## <a name="syntax"></a>Syntaxe

```C
void *_recalloc_dbg(
   void *userData,
   size_t num,
   size_t size,
   int blockType,
   const char *filename,
   int linenumber
);
```

### <a name="parameters"></a>Parametry

*UserData*<br/>
Ukazatel na dříve přidělenou paměť bloku.

*Číslo*<br/>
Požadovaný počet bloky paměti.

*Velikost*<br/>
Požadovaná velikost každého bloku paměti (v bajtech).

*blockType*<br/>
Požadovaný typ bloku paměti: **_client_block –** nebo **_normal_block –**.

Informace o typech bloku přidělení a způsobu jejich použití naleznete v tématu [typy bloků v haldě ladění](/visualstudio/debugger/crt-debug-heap-details).

*Název souboru*<br/>
Ukazatel na název zdrojového souboru, který požadovanou operaci přidělení nebo **NULL**.

*lineNumber*<br/>
Číslo řádku na zdrojový soubor, kde byla vyžádána operace přidělení nebo **NULL**.

*Filename* a *linenumber* parametry jsou k dispozici pouze při **_recalloc_dbg –** explicitně volané nebo [_crtdbg_map_alloc –](../../c-runtime-library/crtdbg-map-alloc.md) preprocesoru konstanta byla definována.

## <a name="return-value"></a>Návratová hodnota

Při úspěšném dokončení této funkce buď vrací ukazatel na část uživatele k opětovnému přidělení paměti bloku, volá nové funkce obslužné rutiny nebo vrátí **NULL**. Úplný popis návratový chování najdete v následující části poznámky. Další informace o používání nové funkce obslužné rutiny najdete v tématu [_recalloc –](recalloc.md) funkce.

## <a name="remarks"></a>Poznámky

**_recalloc_dbg –** je ladicí verze [_recalloc –](recalloc.md) funkce. Když [_DEBUG –](../../c-runtime-library/debug.md) není definován, každé volání **_recalloc_dbg –** byla snížena volání **_recalloc –**. Obě **_recalloc –** a **_recalloc_dbg –** znovu přidělte blok paměti základní haldy, ale **_recalloc_dbg –** může vyrovnávat několik funkce ladění: vyrovnávací paměti na obou stranách část bloku chcete otestovat nevracení uživatelským blok zadejte parametr sledovat konkrétní přidělení typy a *filename*/*linenumber* informací k určení původ požadavků na přidělení.

**_recalloc_dbg –** přidělí blok zadaná paměťová se něco víc místa, než požadovaná velikost (*číslo* * *velikost*) který může být větší nebo menší než velikost původně přidělenou paměť bloku. Další prostor se používá správce haldy ladění propojení bloky paměti ladění a k poskytování aplikace s informace o ladění záhlaví a přepsat vyrovnávací paměti. Přerozdělení může způsobit přesunutí původní bloku paměti do jiného umístění v haldě, jakož i změníte velikost bloku paměti. Část uživatele bloku je vyplněnou hodnotou 0xCD a každý z vyrovnávací paměti přepsat jsou vyplněny 0xFD.

**_recalloc_dbg –** nastaví **errno** k **enomem –** Pokud selže přidělení paměti; **Einval –** je vrácena, pokud objem paměti vyžadované (včetně režie, již bylo zmíněno dříve) přesahuje **_heap_maxreq –**. Informace o tomto a dalších kódy chyb naleznete v tématu [errno, _doserrno –, _sys_errlist – a _sys_nerr –](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

Informace o tom, jak jsou bloky paměti přidělené, inicializovat a spravovat ladicí verze základní heap najdete v tématu [podrobnosti haldy ladění CRT](/visualstudio/debugger/crt-debug-heap-details). Informace o rozdílech mezi volání funkce standardní haldy a jeho ladicí verze v sestavení ladicí verze aplikace, najdete v tématu [ladění verzí z funkcí přidělení haldy](/visualstudio/debugger/debug-versions-of-heap-allocation-functions).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_recalloc_dbg**|\<crtdbg.h>|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Ladicí verze [běhové knihovny jazyka C](../../c-runtime-library/crt-library-features.md) pouze.

## <a name="see-also"></a>Viz také

[Rutiny ladění](../../c-runtime-library/debug-routines.md)<br/>
