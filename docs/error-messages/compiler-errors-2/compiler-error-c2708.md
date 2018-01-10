---
title: "C2708 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2708
dev_langs: C++
helpviewer_keywords: C2708
ms.assetid: d52d3088-1141-42f4-829c-74755a7fcc3a
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 495fd9aeaad785edd8653e46ae666f60c337b12d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2708"></a>C2708 chyby kompilátoru
"identifikátor": parametry skutečná délka v bajtech se liší od předchozího volání nebo odkaz  
  
 A [__stdcall](../../cpp/stdcall.md) funkce musí předcházet prototypu. Jinak Kompilátor interpretuje první volání funkce jako prototyp a k této chybě dojde, když kompilátor narazí volání, která neodpovídá.  
  
 Opravit tuto chybu přidat funkce prototypu.