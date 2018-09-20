---
title: 3.1.8 omp_get_dynamic – funkce | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: c03e2daf-29c9-49e3-9b67-b980ad1ab195
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2c30f49eaf91353d6a7cd9bd26e0e10e95cb6acd
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46426780"
---
# <a name="318-ompgetdynamic-function"></a>3.1.8 omp_get_dynamic – funkce

**Omp_get_dynamic –** funkce vrací nenulovou hodnotu, pokud je povolené dynamické přizpůsobení vlákna a v opačném případě vrátí 0. Formát je následujícím způsobem:

```
#include <omp.h>
int omp_get_dynamic(void);
```

Implementace neimplementuje dynamické úpravy počtu vláken, tato funkce vždy vrátí hodnotu 0.

## <a name="cross-references"></a>Křížové odkazy:

- Popis nastavení dynamické vlákno, naleznete v tématu [části 3.1.7](../../parallel/openmp/3-1-7-omp-set-dynamic-function.md) na stránce 39.