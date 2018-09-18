---
title: Chyba Linkerů LNK1140 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1140
dev_langs:
- C++
helpviewer_keywords:
- LNK1140
ms.assetid: 468d7651-a7cd-47b9-aead-5bb2fab56121
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9f850360bc749a41e548cebae9f58f9fc7d3d420
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46044701"
---
# <a name="linker-tools-error-lnk1140"></a>Chyba linkerů LNK1140

příliš moc modulů pro databáze programu. Propojte pomocí/pdb: NONE

Projekt obsahuje více než 4096 moduly.

### <a name="to-fix-by-using-the-following-possible-solutions"></a>Chcete-li vyřešit pomocí následujících možná řešení

1. Znovu propojit pomocí [/pdb: NONE](../../build/reference/pdb-use-program-database.md).

1. Některé moduly kompilaci bez informací o ladění.

1. Snížit počet modulů.