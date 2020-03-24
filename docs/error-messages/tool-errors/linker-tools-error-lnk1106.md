---
title: Chyba linkerů LNK1106
ms.date: 11/04/2016
f1_keywords:
- LNK1106
helpviewer_keywords:
- LNK1106
ms.assetid: 528f7e65-04be-4966-b8af-9276837c7cda
ms.openlocfilehash: 091d4e173bfb2eff8ffee2b5c30647f4d5e3bc04
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80195367"
---
# <a name="linker-tools-error-lnk1106"></a>Chyba linkerů LNK1106

Neplatný soubor nebo disk je plný: nejde vyhledat umístění.

Nástroj nemůže číst nebo zapisovat do `location` v souboru mapované paměti.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Opravu provedete kontrolou následujících možných příčin.

1. Disk je plný.

   Uvolněte místo a znovu propojte.

1. Probíhá pokus o připojení přes síť.

   Některé sítě plně nepodporují soubory mapované paměti používané linkerem. Zkuste propojit místní disk.

1. Chybný blok na disku.

   I když by se u operačního systému a disku zjistila taková chyba, možná budete chtít spustit program pro kontrolu disků.

1. Nedostatek prostoru v haldě.

   Další informace najdete v tématu [C1060](../../error-messages/compiler-errors-1/fatal-error-c1060.md) .
