---
title: C3728 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3728
dev_langs:
- C++
helpviewer_keywords:
- C3728
ms.assetid: 6b510cb1-887f-4fcd-9a1f-3bb720417ed1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bae204db616db9e7d7e04cfd62d53374b0793aa9
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3728"></a>C3728 chyby kompilátoru
'událost': událostí nemá vyvolat metodu  
  
 Metadata vytvořeny s jazykem, například C#, který neumožňuje událost má být aktivována z mimo třídu, ve které byla definována, byla zahrnuta [#using](../../preprocessor/hash-using-directive-cpp.md) směrnice a program Visual C++ pomocí CLR – programování se pokusil vyvolání události.  
  
 Třída obsahující událost vyvolat událost v programu vyvinuté v jazyce, například C#, musí také definovat veřejnou metodu, která vyvolává událost.