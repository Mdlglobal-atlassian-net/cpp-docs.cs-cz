---
title: C2708 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2708
dev_langs:
- C++
helpviewer_keywords:
- C2708
ms.assetid: d52d3088-1141-42f4-829c-74755a7fcc3a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d30b2e5c1856a604ae314316cd71d6acc00a7c74
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33234757"
---
# <a name="compiler-error-c2708"></a>C2708 chyby kompilátoru
"identifikátor": parametry skutečná délka v bajtech se liší od předchozího volání nebo odkaz  
  
 A [__stdcall](../../cpp/stdcall.md) funkce musí předcházet prototypu. Jinak Kompilátor interpretuje první volání funkce jako prototyp a k této chybě dojde, když kompilátor narazí volání, která neodpovídá.  
  
 Opravit tuto chybu přidat funkce prototypu.