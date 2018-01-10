---
title: "offsetof – makro | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
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
f1_keywords: offsetof
dev_langs: C++
helpviewer_keywords:
- structure members, offset
- offsetof macro
ms.assetid: f3b4eb16-a882-4d38-afc9-eebd976a7352
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: d99947615f2f24116f3d9b64e94daba60c848ec4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="offsetof-macro"></a>offsetof – makro
Načte posun členem od začátku jeho nadřazené struktury.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      size_t offsetof(  
   structName,  
   memberName   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 *structName*  
 Název nadřazeného datovou strukturu.  
  
 `memberName`  
 Název člena v nadřazené datovou strukturu pro které chcete určit posun.  
  
## <a name="return-value"></a>Návratová hodnota  
 `offsetof`Vrátí posun od začátku její nadřazená struktura dat v bajtech zadaného člena. Je definován pro bitových polí.  
  
## <a name="remarks"></a>Poznámky  
 `offsetof` Makro Vrátí posun v bajtech `memberName` od začátku struktury určeného *structName* jako hodnota typu `size_t`. Můžete určit typy s `struct` – klíčové slovo.  
  
> [!NOTE]
>  `offsetof`není funkce a nelze popsat pomocí C prototypu.  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`offsetof`|\<stddef.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md) v úvodu.  
  
## <a name="libraries"></a>Knihovny  
 Všechny verze [běhové knihovny jazyka C](../../c-runtime-library/crt-library-features.md).  
  
## <a name="see-also"></a>Viz také  
 [Přidělení paměti](../../c-runtime-library/memory-allocation.md)