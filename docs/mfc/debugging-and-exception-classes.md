---
title: Třídy ladění a výjimek | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.classes.debug
dev_langs:
- C++
helpviewer_keywords:
- debugging [MFC], exception classes
- debugging [MFC], classes for debugging
ms.assetid: 0d158efd-2e62-452e-9d2a-d3c30dfee7f9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4b7c88c5d12f56318bbb37a825e28c2bfcbc132d
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46418174"
---
# <a name="debugging-and-exception-classes"></a>Třídy ladění a výjimek

Tyto třídy poskytují podporu pro ladění dynamické přidělování paměti a pro předávání informací výjimky z funkce, kde je vyvolána výjimka funkci kde je zachycena.

Použití tříd [CDumpContext](../mfc/reference/cdumpcontext-class.md) a [cmemorystate –](../mfc/reference/cmemorystate-structure.md) během vývoje vám pomůže s laděním, jak je popsáno v [ladění aplikací MFC](/visualstudio/debugger/mfc-debugging-techniques). Použití [CRuntimeClass](../mfc/reference/cruntimeclass-structure.md) určení třídy libovolného objektu v době běhu, jak je popsáno v článku [přístup k informacím o třídě Run-Time](../mfc/accessing-run-time-class-information.md). Rozhraní používá `CRuntimeClass` dynamicky vytvořit objekty určité třídy.

## <a name="see-also"></a>Viz také

[Přehled tříd](../mfc/class-library-overview.md)

