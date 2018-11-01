---
title: Upozornění kompilátoru prostředků RC4093
ms.date: 11/04/2016
f1_keywords:
- RC4093
helpviewer_keywords:
- RC4093
ms.assetid: 3c61b4a4-b418-465b-a4fd-cb1ff0adb8dd
ms.openlocfilehash: 23bf436e6e8338f89bc576564181c84715028332
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50541879"
---
# <a name="resource-compiler-warning-rc4093"></a>Upozornění kompilátoru prostředků RC4093

znak bez řídícího znaku nového řádku v konstantě znaku v neaktivního kódu

Konstantní výraz `#if`, `#elif`, **#ifdef**, nebo **#ifndef** direktivy preprocesoru vyhodnocen na hodnotu nula, že kód, který následuje neaktivní. V rámci této neaktivního kódu lze znak nového řádku zobrazovaly v rámci jednoduchých nebo dvojitých uvozovek.

Veškerý text až do další dvojité uvozovky se považuje za v konstantě znaku.