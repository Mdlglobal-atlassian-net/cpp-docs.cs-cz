---
title: "C3728 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3728
dev_langs:
- C++
helpviewer_keywords:
- C3728
ms.assetid: 6b510cb1-887f-4fcd-9a1f-3bb720417ed1
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d20a0772a38dadc5956e1d174a23ecb0a8593647
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3728"></a>C3728 chyby kompilátoru
'událost': událostí nemá vyvolat metodu  
  
 Metadata vytvořeny s jazykem, například C#, který neumožňuje událost má být aktivována z mimo třídu, ve které byla definována, byla zahrnuta [#using](../../preprocessor/hash-using-directive-cpp.md) směrnice a program Visual C++ pomocí CLR – programování se pokusil vyvolání události.  
  
 Třída obsahující událost vyvolat událost v programu vyvinuté v jazyce, například C#, musí také definovat veřejnou metodu, která vyvolává událost.