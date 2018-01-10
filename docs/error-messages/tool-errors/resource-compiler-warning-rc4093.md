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
ms.workload: cplusplus
ms.openlocfilehash: 4d21cbba379e72675b8957be58dc712b83673947
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="resource-compiler-warning-rc4093"></a>Upozornění kompilátoru prostředků RC4093
neuvozené nový řádek v konstantě znaku v neaktivní kódu  
  
 Konstantní výraz `#if`, `#elif`, **#ifdef**, nebo **#ifndef** direktivy preprocesoru vyhodnotit na hodnotu nula, což kód, který následuje neaktivní. V rámci této neaktivní kód znak nového řádku zobrazovaly v rámci sady jednoduchých nebo dvojitých uvozovek.  
  
 Celý text, dokud další dvojité uvozovky se považuje za v rámci konstanta znaků.