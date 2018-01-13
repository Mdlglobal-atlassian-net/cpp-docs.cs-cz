---
title: "_Crtsetallochook – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _CrtSetAllocHook
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
- _CrtSetAllocHook
- CrtSetAllocHook
dev_langs: C++
helpviewer_keywords:
- _CrtSetAllocHook function
- CrtSetAllocHook function
ms.assetid: 405df37b-2fd1-42c8-83bc-90887f17f29d
caps.latest.revision: "15"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ac777b2e2a7ca791821be52b68f136998c33d243
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="crtsetallochook"></a>_CrtSetAllocHook
Nainstaluje funkci definované klienta přidělení zapojování do procesu přidělení paměti běhové ladění C (pouze ladicí verze).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
_CRT_ALLOC_HOOK _CrtSetAllocHook(  
   _CRT_ALLOC_HOOK allocHook   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `allocHook`  
 Nové funkce definované klienta přidělení připojí do proces přidělení paměti běhové ladění C.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí funkce háku přidělení dříve definovaném, nebo `NULL` Pokud `allocHook` je `NULL`.  
  
## <a name="remarks"></a>Poznámky  
 `_CrtSetAllocHook`umožňuje aplikaci připojit svůj vlastní funkce přidělení do procesu C ladicí běhové knihovny paměti přidělení. V důsledku toho každých volání funkce ladění přidělení přidělit, znovu přidělte nebo uvolněte aktivační události paměti bloku volání funkce háku aplikace. `_CrtSetAllocHook`poskytuje aplikaci snadno metodu pro testování, jak aplikace zpracovává situacích, není dostatek paměti, možnost zkontrolovat přidělení vzory a příležitost k protokolování informací o přidělení pro pozdější analýzu. Když [_DEBUG –](../../c-runtime-library/debug.md) není definován, volání `_CrtSetAllocHook` jsou odebrány při předběžném zpracování.  
  
 `_CrtSetAllocHook` Funkce nainstaluje nové funkce definované klienta přidělení zadaný v `allocHook` a vrátí funkce háku dříve definované. Následující příklad ukazuje, jak by měla být deklaraci háku přidělení definované klienta:  
  
```  
int YourAllocHook( int allocType, void *userData, size_t size, int   
blockType, long requestNumber, const unsigned char *filename, int   
lineNumber);  
```  
  
 `allocType` Argument určuje typ operace přidělení `(_HOOK_ALLOC`, `_HOOK_REALLOC`, a `_HOOK_FREE`), volání funkce háku přidělení pro aktivaci. Pokud je spouštěcí typ přidělení `_HOOK_FREE`, `userData` ukazatel do datové části uživatele bloku paměti se uvolnit. Nicméně, pokud je spouštěcí typ přidělení `_HOOK_ALLOC` nebo `_HOOK_REALLOC`, `userData` je `NULL` protože dosud nebyl přidělen bloku paměti.  
  
 `size`Určuje velikost paměti blokovat v bajtech `blockType` označuje typ bloku paměti `requestNumber` je objekt přidělení pořadové číslo bloku paměti a pokud je k dispozici, `filename` a `lineNumber` zadejte název zdrojového souboru a Číslo řádku, kde se zahájí spouštěcí operace přidělení.  
  
 Po dokončení zpracování funkce háku musí vrátit logickou hodnotu, která informuje hlavní proces přidělení běhové C, jak chcete pokračovat. Když chce, aby funkce háku přidělení hlavní proces pokračovat, protože pokud funkce háku měl nikdy volat, pak by měla vrátit funkce háku `TRUE`. To způsobí, že původní spouštěcí přidělení operaci provést. Pomocí této implementace funkce háku shromáždit a uložit informace o přidělení pro pozdější analýzu bez zasahování aktuální operace přidělení nebo stavu haldy ladění.  
  
 Když chce, aby funkce háku přidělení hlavní proces pokračovat, protože pokud byla volána spouštěcí operace přidělení a se nezdařilo, pak by měla vrátit funkce háku `FALSE`. Pomocí této implementace funkce háku simulovat širokou škálu podmínky paměti a ladění haldy stavy otestovat, jak aplikace zpracovává každé situaci.  
  
 Zrušte funkce háku, předat `NULL` k `_CrtSetAllocHook`.  
  
 Další informace o tom, `_CrtSetAllocHook` lze použít s další funkce správy paměti nebo napsat vlastní funkce háku definované klienta najdete v tématu [zápis funkce háku ladění](/visualstudio/debugger/debug-hook-function-writing).  
  
> [!NOTE]
>  `_CrtSetAllocHook`není podporován v rámci `/clr:pure`. **/CLR: pure** a **/CLR: safe** – možnosti kompilátoru jsou zastaralé v sadě Visual Studio 2015.  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`_CrtSetAllocHook`|\<crtdbg.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md) v úvodu.  
  
## <a name="libraries"></a>Knihovny  
 Ladicí verze [běhové knihovny jazyka C](../../c-runtime-library/crt-library-features.md) pouze.  
  
## <a name="example"></a>Příklad  
 Příklad, jak pomocí `_CrtSetAllocHook`, najdete v části [crt_dbg2](http://msdn.microsoft.com/en-us/21e1346a-6a17-4f57-b275-c76813089167).  
  
## <a name="see-also"></a>Viz také  
 [Rutiny ladění](../../c-runtime-library/debug-routines.md)   
 [_CrtGetAllocHook](../../c-runtime-library/reference/crtgetallochook.md)