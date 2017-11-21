---
title: "C2818 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2818
dev_langs: C++
helpviewer_keywords: C2818
ms.assetid: 715fc7c9-0c6d-452b-b7f5-1682cea5e907
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 02c1b8e67679e7b8ce69b202c3ddef899439095d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2818"></a>C2818 chyby kompilátoru
použití přetížený -> operátor je rekurzivní prostřednictvím typu "typ"  
  
 Předefinování operátor přístupu členů třídy obsahuje rekurzivního `return` příkaz. Znovu definovat `->` operátor s rekurze, je nutné přesunout rutiny rekurzivní funkci volat z operátor přepsat funkce.