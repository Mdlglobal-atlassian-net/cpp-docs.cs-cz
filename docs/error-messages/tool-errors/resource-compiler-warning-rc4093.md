---
title: "Upozornění kompilátoru prostředků RC4093 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: RC4093
dev_langs: C++
helpviewer_keywords: RC4093
ms.assetid: 3c61b4a4-b418-465b-a4fd-cb1ff0adb8dd
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: b799f43737482ed9491d054adb34e987e75f3a47
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="resource-compiler-warning-rc4093"></a>Upozornění kompilátoru prostředků RC4093
neuvozené nový řádek v konstantě znaku v neaktivní kódu  
  
 Konstantní výraz `#if`, `#elif`, **#ifdef**, nebo **#ifndef** direktivy preprocesoru vyhodnotit na hodnotu nula, což kód, který následuje neaktivní. V rámci této neaktivní kód znak nového řádku zobrazovaly v rámci sady jednoduchých nebo dvojitých uvozovek.  
  
 Celý text, dokud další dvojité uvozovky se považuje za v rámci konstanta znaků.