---
title: _seh_filter_dll _seh_filter_exe | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _XcptFilter
- _seh_filter_dll
- _seh_filter_exe
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
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- XcptFilter
- _XcptFilter
- _seh_filter_dll
- _seh_filter_exe
- corecrt_startup/_seh_filter_exe
- corecrt_startup/_seh_filter_dll
dev_langs: C++
helpviewer_keywords:
- XcptFilter function
- _XcptFilter function
- _seh_filter_dll function
- _seh_filter_exe function
ms.assetid: 747e5963-3a12-4bf5-b5c4-d4c1b6068e15
caps.latest.revision: "14"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 677e203e552dfa2f057cb0631d73c9f48349c4b4
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="sehfilterdll-sehfilterexe"></a>_seh_filter_dll _seh_filter_exe
Identifikuje výjimku a související provést akci.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
int __cdecl _seh_filter_dll(  
   unsigned long _ExceptionNum,  
   struct _EXCEPTION_POINTERS* _ExceptionPtr  
);  
int __cdecl _seh_filter_exe(  
   unsigned long _ExceptionNum,  
   struct _EXCEPTION_POINTERS* _ExceptionPtr  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 [v]`_ExceptionNum`  
 Identifikátor pro výjimku.  
  
 [v]`_ExceptionPtr`  
 Ukazatel na informace o výjimce.  
  
## <a name="return-value"></a>Návratová hodnota  
 Celé číslo, které určuje akce, které mají být provedeny, na základě výsledku zpracování výjimky.  
  
## <a name="remarks"></a>Poznámky  
 Tyto metody jsou volány výraz filtru výjimek [zkuste-except – příkaz](../../cpp/try-except-statement.md). Metoda zajímají konstantní interní tabulku pro identifikaci výjimky a určení příslušné akce, jak je vidět tady. Čísla výjimky jsou definovány v souboru winnt.h a signál čísla, která jsou definována v signal.h.  
  
|Číslo výjimky (dlouho bez znaménka)|Číslo signál|  
|----------------------------------------|-------------------|  
|STATUS_ACCESS_VIOLATION|SIGSEGV –|  
|STATUS_ILLEGAL_INSTRUCTION|SIGILL –|  
|STATUS_PRIVILEGED_INSTRUCTION|SIGILL –|  
|STATUS_FLOAT_DENORMAL_OPERAND|SIGFPE –|  
|STATUS_FLOAT_DIVIDE_BY_ZERO|SIGFPE –|  
|STATUS_FLOAT_INEXACT_RESULT|SIGFPE –|  
|STATUS_FLOAT_INVALID_OPERATION|SIGFPE –|  
|STATUS_FLOAT_OVERFLOW|SIGFPE –|  
|STATUS_FLOAT_STACK_CHECK|SIGFPE –|  
|STATUS_FLOAT_UNDERFLOW|SIGFPE –|  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** corecrt_startup.h  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace funkcí abecedně](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)