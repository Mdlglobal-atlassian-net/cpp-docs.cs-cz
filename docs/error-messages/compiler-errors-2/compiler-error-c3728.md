---
title: "C3728 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3728
dev_langs: C++
helpviewer_keywords: C3728
ms.assetid: 6b510cb1-887f-4fcd-9a1f-3bb720417ed1
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 100ef8275f938406a4f6a7d3909e04f40ce1d16b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3728"></a>C3728 chyby kompilátoru
'událost': událostí nemá vyvolat metodu  
  
 Metadata vytvořeny s jazykem, například C#, který neumožňuje událost má být aktivována z mimo třídu, ve které byla definována, byla zahrnuta [#using](../../preprocessor/hash-using-directive-cpp.md) směrnice a program Visual C++ pomocí CLR – programování se pokusil vyvolání události.  
  
 Třída obsahující událost vyvolat událost v programu vyvinuté v jazyce, například C#, musí také definovat veřejnou metodu, která vyvolává událost.