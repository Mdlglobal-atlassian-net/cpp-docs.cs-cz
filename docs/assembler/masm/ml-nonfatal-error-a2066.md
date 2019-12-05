---
title: Méně závažná chyba nástroje ML A2066
ms.date: 08/30/2018
ms.custom: error-reference
f1_keywords:
- A2066
helpviewer_keywords:
- A2066
ms.assetid: 58220fdf-fb8f-47fc-a36d-737867361185
ms.openlocfilehash: 8dc3000b2edc2b1ecda7cc3952b554296de19aa3
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/05/2019
ms.locfileid: "74855876"
---
# <a name="ml-nonfatal-error-a2066"></a>Méně závažná chyba nástroje ML A2066

**nekompatibilní režim procesoru a velikost segmentu**

Došlo k pokusu o otevření segmentu s atributem **USE16**, **USE32**nebo **Flat** , který není kompatibilní se zadaným procesorem, nebo ke změně na 16bitový procesor v 32ém segmentu.

Před atributy **USE32** a **Flat** musí předcházet direktiva. 386 nebo větší direktiva procesoru.

## <a name="see-also"></a>Viz také:

[Chybové zprávy ML](../../assembler/masm/ml-error-messages.md)<br/>