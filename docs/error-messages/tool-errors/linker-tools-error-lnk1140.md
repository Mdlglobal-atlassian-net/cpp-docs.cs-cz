---
title: Chyba linkerů LNK1140
ms.date: 11/04/2016
f1_keywords:
- LNK1140
helpviewer_keywords:
- LNK1140
ms.assetid: 468d7651-a7cd-47b9-aead-5bb2fab56121
ms.openlocfilehash: 48c735f29918c4d1caeb15123f7376276d116fb4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50482461"
---
# <a name="linker-tools-error-lnk1140"></a>Chyba linkerů LNK1140

příliš moc modulů pro databáze programu. Propojte pomocí/pdb: NONE

Projekt obsahuje více než 4096 moduly.

### <a name="to-fix-by-using-the-following-possible-solutions"></a>Chcete-li vyřešit pomocí následujících možná řešení

1. Znovu propojit pomocí [/pdb: NONE](../../build/reference/pdb-use-program-database.md).

1. Některé moduly kompilaci bez informací o ladění.

1. Snížit počet modulů.