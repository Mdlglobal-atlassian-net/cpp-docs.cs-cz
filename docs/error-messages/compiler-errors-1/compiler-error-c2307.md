---
title: Chyba kompilátoru C2307
ms.date: 11/04/2016
f1_keywords:
- C2307
helpviewer_keywords:
- C2307
ms.assetid: ce6c8033-a673-4679-9883-bedec36ae385
ms.openlocfilehash: a9d5addc18dd548e584a1cceed8b880cb62ed40d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80206276"
---
# <a name="compiler-error-c2307"></a>Chyba kompilátoru C2307

Direktiva pragma pragma musí být mimo funkci, pokud je povolená přírůstková kompilace.

Pokud používáte přírůstkovou kompilaci, je nutné umístit direktivu pragma `data_seg` mezi Functions.
