---
title: Upozornění kompilátoru prostředků RC4093 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- RC4093
dev_langs:
- C++
helpviewer_keywords:
- RC4093
ms.assetid: 3c61b4a4-b418-465b-a4fd-cb1ff0adb8dd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e9cca3c2a139e1109746f3a690cfb3f31509a9fe
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="resource-compiler-warning-rc4093"></a>Upozornění kompilátoru prostředků RC4093
neuvozené nový řádek v konstantě znaku v neaktivní kódu  
  
 Konstantní výraz `#if`, `#elif`, **#ifdef**, nebo **#ifndef** direktivy preprocesoru vyhodnotit na hodnotu nula, což kód, který následuje neaktivní. V rámci této neaktivní kód znak nového řádku zobrazovaly v rámci sady jednoduchých nebo dvojitých uvozovek.  
  
 Celý text, dokud další dvojité uvozovky se považuje za v rámci konstanta znaků.