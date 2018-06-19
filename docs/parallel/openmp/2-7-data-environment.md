---
title: 2.7 datové prostředí | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 74e44b3c-e18c-4773-8e78-cd6c4413ae57
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d1b0f253ce14ffc5d3740e582a9a51feea56ad32
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33690062"
---
# <a name="27-data-environment"></a>2.7 Datové prostředí
Tato část představuje direktivu a několik klauzule řízení prostředí dat během provádění paralelní oblastech, následujícím způsobem:  
  
-   A **threadprivate** – direktiva (najdete v následující části) zajišťuje nastavit rozsah souboru, obor názvů nebo statický rozsah bloku proměnné místní na vlákno.  
  
-   Věty, které může být určen na direktivy k řízení sdílení atributy proměnných po dobu trvání konstrukce paralelní nebo sdílení práce jsou popsané v [části 2.7.2](../../parallel/openmp/2-7-2-data-sharing-attribute-clauses.md) na stránce 25.