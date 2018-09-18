---
title: Upozornění kompilátoru prostředků RC4093 | Dokumentace Microsoftu
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
ms.openlocfilehash: 9b1ca04b17ebdb9d48bc94032482caf48ad4aa00
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46111560"
---
# <a name="resource-compiler-warning-rc4093"></a>Upozornění kompilátoru prostředků RC4093

znak bez řídícího znaku nového řádku v konstantě znaku v neaktivního kódu

Konstantní výraz `#if`, `#elif`, **#ifdef**, nebo **#ifndef** direktivy preprocesoru vyhodnocen na hodnotu nula, že kód, který následuje neaktivní. V rámci této neaktivního kódu lze znak nového řádku zobrazovaly v rámci jednoduchých nebo dvojitých uvozovek.

Veškerý text až do další dvojité uvozovky se považuje za v konstantě znaku.