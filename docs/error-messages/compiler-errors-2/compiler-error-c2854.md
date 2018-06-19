---
title: C2854 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2854
dev_langs:
- C++
helpviewer_keywords:
- C2854
ms.assetid: 917fec9c-790a-4149-8dfc-00d17a09199c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1555d36a9371145af2685ecd6650d7fdecc69660
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33243615"
---
# <a name="compiler-error-c2854"></a>C2854 chyby kompilátoru
Chyba syntaxe v hdrstop – #pragma  
  
 `#pragma hdrstop` Obsahuje neplatný název souboru. – Direktiva pragma může následovat volitelný název souboru v kulaté závorky a uvozovky:  
  
 Následující ukázka generuje C2854:  
  
```  
// C2854.cpp  
// compile with: /c  
#pragma hdrstop( "\\source\\pchfiles\\myheader.pch" ]   // C2854  
// try the following line instead  
// #pragma hdrstop( "\\source\\pchfiles\\myheader.pch" )  
```