---
title: C.1 Zápis
ms.date: 11/04/2016
ms.assetid: a23b2631-8096-4bf3-ac23-ba4f4bd7a52a
ms.openlocfilehash: 593450b6dd7dcb30adbf8546ad96ff716c6fbc1c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50473980"
---
# <a name="c1-notation"></a>C.1 Zápis

Gramatika pravidla jsou založená na názvu bez terminal, za nímž následuje dvojtečka, následovaný nahrazení alternativy na samostatných řádcích.

Syntaktické výraz<sub>optimalizované</sub> znamená, že je výraz nepovinný v nahrazení.

Syntaktické výraz *termín*<sub>optseq</sub> je ekvivalentní *termín seq*<sub>optimalizované</sub> s následující další pravidla:

*termín seq* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Termín*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*termín seq* *termín*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*termín seq* **,** *termín*