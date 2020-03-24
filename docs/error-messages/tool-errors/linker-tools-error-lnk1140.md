---
title: Chyba linkerů LNK1140
ms.date: 11/04/2016
f1_keywords:
- LNK1140
helpviewer_keywords:
- LNK1140
ms.assetid: 468d7651-a7cd-47b9-aead-5bb2fab56121
ms.openlocfilehash: 845c796ee9611e921e2fd1707b9bb956ab62a5ac
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80195263"
---
# <a name="linker-tools-error-lnk1140"></a>Chyba linkerů LNK1140

příliš mnoho modulů pro databázi programu; propojit s/PDB: žádné

Projekt obsahuje více než 4096 modulů.

### <a name="to-fix-by-using-the-following-possible-solutions"></a>Oprava pomocí následujících možných řešení

1. Znovu propojte pomocí [/PDB: none](../../build/reference/pdb-use-program-database.md).

1. Zkompilujte některé moduly bez ladicích informací.

1. Snižte počet modulů.
