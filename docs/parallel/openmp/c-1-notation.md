---
title: C.1 zápis | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: a23b2631-8096-4bf3-ac23-ba4f4bd7a52a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4bbb3190dd5aa32315cd8f402f92fd94893b4b27
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46411869"
---
# <a name="c1-notation"></a>C.1 Zápis

Gramatika pravidla jsou založená na názvu bez terminal, za nímž následuje dvojtečka, následovaný nahrazení alternativy na samostatných řádcích.

Syntaktické výraz<sub>optimalizované</sub> znamená, že je výraz nepovinný v nahrazení.

Syntaktické výraz *termín*<sub>optseq</sub> je ekvivalentní *termín seq*<sub>optimalizované</sub> s následující další pravidla:

*termín seq* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Termín*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*termín seq* *termín*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*termín seq* **,** *termín*