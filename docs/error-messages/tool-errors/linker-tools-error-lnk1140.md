---
title: Chyba linkerů LNK1140
ms.date: 11/04/2016
f1_keywords:
- LNK1140
helpviewer_keywords:
- LNK1140
ms.assetid: 468d7651-a7cd-47b9-aead-5bb2fab56121
ms.openlocfilehash: 48c735f29918c4d1caeb15123f7376276d116fb4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62255063"
---
# <a name="linker-tools-error-lnk1140"></a>Chyba linkerů LNK1140

příliš moc modulů pro databáze programu. Propojte pomocí/pdb: NONE

Projekt obsahuje více než 4096 moduly.

### <a name="to-fix-by-using-the-following-possible-solutions"></a>Chcete-li vyřešit pomocí následujících možná řešení

1. Znovu propojit pomocí [/pdb: NONE](../../build/reference/pdb-use-program-database.md).

1. Některé moduly kompilaci bez informací o ladění.

1. Snížit počet modulů.