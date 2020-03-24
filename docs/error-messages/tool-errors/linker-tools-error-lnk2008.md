---
title: Chyba linkerů LNK2008
ms.date: 11/04/2016
f1_keywords:
- LNK2008
helpviewer_keywords:
- LNK2008
ms.assetid: bbcd83c5-c8ae-439e-a033-63643a5bb373
ms.openlocfilehash: c7794d09f7eeb9dceba7098ca7af90ccf2eeccad
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80194821"
---
# <a name="linker-tools-error-lnk2008"></a>Chyba linkerů LNK2008

Cíl opravy není zarovnaný symbol_name.

ODKAZ nalezl v souboru objektu cíl opravy, který nebyl správně zarovnán.

Tato chyba může být způsobena vlastním zarovnáním secton (například #pragma [Pack](../../preprocessor/pack.md)), modifikátorem [Zarovnání](../../cpp/align-cpp.md) nebo pomocí kódu jazyka sestavení, který upravuje secton zarovnání.

Pokud váš kód nepoužívá žádný z výše uvedených, může to být způsobeno kompilátorem.
