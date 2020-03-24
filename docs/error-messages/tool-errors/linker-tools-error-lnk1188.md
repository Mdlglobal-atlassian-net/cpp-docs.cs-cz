---
title: Chyba linkerů LNK1188
ms.date: 11/04/2016
f1_keywords:
- LNK1188
helpviewer_keywords:
- LNK1188
ms.assetid: 4af574b0-5b41-4580-9a37-52a634add995
ms.openlocfilehash: b18a93c7434ee3d66f42829f373bd916a65369bd
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80195172"
---
# <a name="linker-tools-error-lnk1188"></a>Chyba linkerů LNK1188

BADFIXUPSECTION:: Neplatný cíl opravy – symbol; Možná část s nulovou délkou

Během připojení VxD neobsahoval cíl přemístění žádný oddíl. U LINK386 (starší verze) se možná použil záznam skupiny OMF (generovaný direktivou MASM skupiny) pro kombinování oddílu s nulovou délkou s jinou nenulovou délkou. Formát COFF nepodporuje oddíly direktivy GROUP a Zero Length. Když propojení automaticky převede tento typ OMF objektů na COFF, může dojít k této chybě.
