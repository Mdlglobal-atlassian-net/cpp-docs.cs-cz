---
title: C3208 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3208
dev_langs:
- C++
helpviewer_keywords:
- C3208
ms.assetid: 6d060bfe-52cf-4599-8f70-bdeb5a670df3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fead75aa4eb245bb6be924ae5f04e1ce28cd8206
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33251645"
---
# <a name="compiler-error-c3208"></a>C3208 chyby kompilátoru
'function': seznam parametrů šablony pro třídu šablony 'class' neodpovídá seznam parametrů šablony pro parametr šablony šablony "parametr"  
  
 Parametr šablony šablona nemá stejný počet parametrů šablony jako šablona zadané třídy.  
  
 Následující ukázka generuje C3208:  
  
```  
// C3208.cpp  
template <template <class T> class TT >  
int f();  
  
template <class T1, class T2>  
struct S;  
  
template <class T1>  
struct R;  
  
int i = f<S>();   // C3208  
// try the following line instead  
// int i = f<R>();  
```