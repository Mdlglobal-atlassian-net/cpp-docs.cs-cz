---
title: Chyba linkerů LNK1241
ms.date: 11/04/2016
f1_keywords:
- LNK1241
helpviewer_keywords:
- LNK1241
ms.assetid: 7b8b52eb-0231-4521-b52a-2bce8d3e8956
ms.openlocfilehash: 6e2b955787166c94be4ca35e1c58df5becd243f2
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80183810"
---
# <a name="linker-tools-error-lnk1241"></a>Chyba linkerů LNK1241

zdrojový soubor již byl určen.

Tato chyba je vygenerována, pokud spouštíte **CVTRES** ručně z příkazového řádku a Pokud předáte výsledný soubor. obj do linkeru kromě dalších souborů. res.

Chcete-li zadat více souborů. res, předejte je do linkeru jako soubory. res, nikoli ze souborů. obj vytvořených pomocí **CVTRES**.
