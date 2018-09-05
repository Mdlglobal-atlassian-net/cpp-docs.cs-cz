---
title: Určení modelu vláken pro projekt (ATL) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- _ATL_FREE_THREADED macro
- _ATL_APARTMENT_THREADED macro
- ATL, multithreading
- threading [ATL], models
- _ATL_SINGLE_THREADED macro
ms.assetid: 6b571078-521c-4f3e-9f08-482aa235a822
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f8a37a3ec730b727f6e214aafad1a4acc65b1dc3
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43760026"
---
# <a name="specifying-the-threading-model-for-a-project-atl"></a>Určení modelu vláken pro projekt (ATL)

K určení modelu vláken projektu ATL k dispozici jsou následující makra:

|– Makro|Pokyny k použití|
|-----------|--------------------------|
|_ATL_SINGLE_THREADED|Určete, zda všechny objekty používat jeden model vláken.|
|_ATL_APARTMENT_THREADED|Určete, zda jeden nebo více objektů použít podprocesový model apartment.|
|_ATL_FREE_THREADED|Určete, zda jeden nebo více objektů pomocí bezplatné nebo neutrální dělení na vlákna. Stávajícího kódu mohou obsahovat odkazy na ekvivalentní – makro [_ATL_MULTI_THREADED](reference/compiler-options-macros.md#_atl_multi_threaded).|

Pokud není definován žádný z těchto maker pro váš projekt, _ATL_FREE_THREADED, nebudou platit.

Makra ovlivnit výkon za běhu následujícím způsobem:

- Určení makra, které odpovídá k objektům ve vašem projektu může zlepšit výkon za běhu.

- Určení vyšší úroveň makra, například při zadání _ATL_APARTMENT_THREADED, když všechny objekty jsou jeden zřetězený, budou mírně snížit výkon za běhu.

- Určení nižší úroveň makra, například pokud zadáte _ATL_SINGLE_THREADED, pokud jeden nebo více objektů použijte podprocesový model apartment nebo volných vláken, může způsobit selhání za běhu aplikace.

Zobrazit [možnosti, Průvodce jednoduchý objekt knihovny ATL](../atl/reference/options-atl-simple-object-wizard.md) popis práce s vlákny modely k dispozici pro objekt knihovny ATL.

## <a name="see-also"></a>Viz také

[Koncepty](../atl/active-template-library-atl-concepts.md)

