---
title: Méně závažná chyba nástroje ML A2066
ms.date: 12/17/2019
ms.custom: error-reference
f1_keywords:
- A2066
helpviewer_keywords:
- A2066
ms.assetid: 58220fdf-fb8f-47fc-a36d-737867361185
ms.openlocfilehash: 4c7c32264fe5daa6cd4e14f47cff111899e8f8d6
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/20/2019
ms.locfileid: "75316886"
---
# <a name="ml-nonfatal-error-a2066"></a>Méně závažná chyba nástroje ML A2066

**nekompatibilní režim procesoru a velikost segmentu**

Došlo k pokusu o otevření segmentu s atributem **USE16**, **USE32**nebo **Flat** , který není kompatibilní se zadaným procesorem, nebo ke změně na 16bitový procesor v 32ém segmentu.

Před atributy **USE32** a **Flat** musí předcházet direktiva. 386 nebo větší direktiva procesoru.

## <a name="see-also"></a>Viz také:

[Chybové zprávy ML](ml-error-messages.md)
