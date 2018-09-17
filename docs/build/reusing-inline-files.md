---
title: Opětovné použití vložených souborů | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- inline files, reusing NMAKE
- revising inline files
- NMAKE program, inline files
ms.assetid: d42dbffb-2cef-4ccb-9a1f-20b8ef81481c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 37544db8076d40e638b6ddf6f340070298229149
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45722459"
---
# <a name="reusing-inline-files"></a>Opětovné použití vložených souborů

Pro opětovné použití vloženého souboru, zadejte <<*filename* tam, kde je soubor definované a nejprve použít, pak znovu použít *filename* bez << dále v stejného nebo jiného příkazu. Příkaz pro vytvoření vložený soubor se musí spustit před všechny příkazy, které používají tento soubor.

## <a name="see-also"></a>Viz také

[Soubory vložené do souboru pravidel](../build/inline-files-in-a-makefile.md)