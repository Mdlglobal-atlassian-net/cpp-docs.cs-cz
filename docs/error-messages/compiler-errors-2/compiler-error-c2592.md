---
title: Chyba kompilátoru C2592 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2592
dev_langs:
- C++
helpviewer_keywords:
- C2592
ms.assetid: 833a4d7b-66ef-4d4c-ae83-a533c2b0eb07
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3f2377f48eb8102771705f2dedc67a7a15f6fa95
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46030979"
---
# <a name="compiler-error-c2592"></a>Chyba kompilátoru C2592

'class': "base_class_2" je zděděno od "base_class_1" a nejde znova specifikovat

Můžete nastavit jenom základní třídy, které nejsou odvozeny z jiných základních tříd. V takovém případě pouze `base_class_1` je potřeba ve specifikaci `class` protože `base_class_1` již dědí `base_class_2`.