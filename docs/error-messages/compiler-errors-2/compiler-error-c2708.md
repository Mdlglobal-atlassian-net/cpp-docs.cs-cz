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
ms.openlocfilehash: 8ce9eb29c776c7d98a7fbad4dc95959180045256
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2708"></a>C2708 chyby kompilátoru
"identifikátor": parametry skutečná délka v bajtech se liší od předchozího volání nebo odkaz  
  
 A [__stdcall](../../cpp/stdcall.md) funkce musí předcházet prototypu. Jinak Kompilátor interpretuje první volání funkce jako prototyp a k této chybě dojde, když kompilátor narazí volání, která neodpovídá.  
  
 Opravit tuto chybu přidat funkce prototypu.