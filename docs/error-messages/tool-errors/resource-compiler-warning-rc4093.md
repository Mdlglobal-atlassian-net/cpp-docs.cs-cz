---
title: Upozornění kompilátoru prostředků RC4093
ms.date: 11/04/2016
f1_keywords:
- RC4093
helpviewer_keywords:
- RC4093
ms.assetid: 3c61b4a4-b418-465b-a4fd-cb1ff0adb8dd
ms.openlocfilehash: 29d24f1e380f5c531e170e5dc23cf5c77eefb874
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80182289"
---
# <a name="resource-compiler-warning-rc4093"></a>Upozornění kompilátoru prostředků RC4093

neřídicí nový řádek v konstantě znaků v neaktivním kódu

Konstantní výraz pro direktivy preprocesoru `#if`, `#elif`, **#ifdef**nebo **#ifndef** vyhodnocený jako nula, takže kód, který následuje za neaktivní. V tomto neaktivním kódu se objevil znak nového řádku v rámci sady jednoduchých nebo dvojitých uvozovek.

Veškerý text, dokud se následující dvojité uvozovky nepovažují za znaková konstanta.
