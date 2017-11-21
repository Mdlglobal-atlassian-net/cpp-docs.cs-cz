---
title: "_Crtisvalidpointer – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _CrtIsValidPointer
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
- CrtlsValidPointer
- _CrtIsValidPointer
dev_langs: C++
helpviewer_keywords:
- CrtIsValidPointer function
- _CrtIsValidPointer function
ms.assetid: 91c35590-ea5e-450f-a15d-ad8d62ade1fa
caps.latest.revision: "13"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: ba249bc78b2e6b6aac95bef2c39b0d9526489ec9
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="crtisvalidpointer"></a>_CrtIsValidPointer
Ověřuje, že ukazatel není null. Ve verzích běhové knihovny jazyka C před Visual Studio 2010 ověřuje, že zadaná paměťová rozsah je platný pro čtení a zápis (pouze ladicí verze).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
int _CrtIsValidPointer(   
   const void *address,  
   unsigned int size,  
   int access   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 adresa  
 Bodů na začátek rozsahu paměti k testování platnosti.  
  
 `size`  
 Velikost zadaná paměťová rozsahu (v bajtech).  
  
 access  
 Usnadnění přístupu pro čtení a zápis k určení rozsahu paměti.  
  
## <a name="return-value"></a>Návratová hodnota  
 `_CrtIsValidPointer`Vrátí hodnotu TRUE, pokud není zadaný ukazatele null. Ve verzi knihovny CRT před Visual Studio 2010 vrátí hodnotu TRUE, pokud paměti rozsah je platný pro zadanou operaci nebo operace. Funkce, jinak vrátí hodnotu FALSE.  
  
## <a name="remarks"></a>Poznámky  
 Od verze knihovny CRT v sadě Visual Studio 2010, parametry velikost a přístupu jsou ignorovány, a `_CrtIsValidPointer` pouze ověřuje, že zadaná adresa není null. Protože tento test je snadné provést sami, nedoporučujeme používat tuto funkci. Ve verzi před Visual Studio 2010, funkce ověřuje, že rozsah paměti začínající na `address` a rozšíření pro `size` bajty je platný pro zadaný usnadnění operaci nebo operace. Když `access` je nastavena na hodnotu TRUE, rozsah paměti ověření pro čtení i zápis. Když `access` hodnotu FALSE, rozsah paměti je ověřen pouze pro čtení. Když [_DEBUG –](../../c-runtime-library/debug.md) není definován, volání `_CrtIsValidPointer` jsou odebrány při předběžném zpracování.  
  
 Protože tato funkce vrátí hodnotu TRUE nebo FALSE, mohla být předána do jednoho z [_ASSERT](../../c-runtime-library/reference/assert-asserte-assert-expr-macros.md) makra pro vytváření jednoduchých ladění chyba mechanismu pro zpracování. Následující příklad způsobí, že výraz je neplatný. Pokud oblast paměti není platná pro čtení i zápis operace:  
  
```  
_ASSERTE( _CrtIsValidPointer( address, size, TRUE ) );  
```  
  
 Další informace o tom, `_CrtIsValidPointer` lze použít s další funkce ladění a makra najdete v tématu [makra pro vytváření sestav](/visualstudio/debugger/macros-for-reporting). Informace o tom, jak jsou bloky paměti přidělené, inicializovat a spravovat ladicí verze základní heap najdete v tématu [podrobnosti haldy ladění CRT](/visualstudio/debugger/crt-debug-heap-details).  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`_CrtIsValidPointer`|\<crtdbg.h >|  
  
 `_CrtIsValidPointer`představuje rozšíření Microsoft. Informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).  
  
## <a name="libraries"></a>Knihovny  
 Ladicí verze [běhové knihovny jazyka C](../../c-runtime-library/crt-library-features.md) pouze.  
  
## <a name="example"></a>Příklad  
 Podívejte se příklad [_crtisvalidheappointer –](../../c-runtime-library/reference/crtisvalidheappointer.md) tématu.  
  
## <a name="see-also"></a>Viz také  
 [Rutiny ladění](../../c-runtime-library/debug-routines.md)