---
title: __setusermatherr | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
apiname:
- __setusermatherr
apilocation:
- msvcr80.dll
- msvcr90.dll
- msvcrt.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr100.dll
- api-ms-win-crt-math-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- __setusermatherr
dev_langs:
- C++
helpviewer_keywords:
- __setusermatherr
ms.assetid: f306818d-381a-4d68-8739-71b92bacb5ea
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4384d67060d2f5d992c098841f76a6b858b78c15
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32408130"
---
# <a name="setusermatherr"></a>__setusermatherr
Určuje uživatelem zadané rountine se budou zpracovávat chyby matematické, místo [_matherr –](../c-runtime-library/reference/matherr.md) rutiny.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
void __setusermatherr(  
   _HANDLE_MATH_ERROR pf   
   )  
```  
  
#### <a name="parameters"></a>Parametry  
 `pf`  
 Ukazatel na implementaci `_matherr` který je zadaný uživatelem.  
  
 Typ `pf` parametr je deklarován jako `typedef int (__cdecl * _HANDLE_MATH_ERROR)(struct _exception *)`.  
  
## <a name="remarks"></a>Poznámky  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|__setusermatherr|matherr.c|