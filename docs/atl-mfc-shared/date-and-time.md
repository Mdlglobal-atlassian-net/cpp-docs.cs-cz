---
title: Datum a čas | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- time, MFC programming
- time
- MFC, date and time
- dates, MFC
ms.assetid: ecf56dc5-d418-4603-ad3e-af7e205a6403
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9753578de006ed46719d94d5861035ab77dbca6c
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43752249"
---
# <a name="date-and-time"></a>Datum a čas

MFC podporuje několika různými způsoby práce s daty a časy. Zde jsou některé z nich:

- Pro obecné účely čas třídy. [CTime](../atl-mfc-shared/reference/ctime-class.md) a [ctimespan –](../atl-mfc-shared/reference/ctimespan-class.md) zapouzdřují většinu funkcí, které jsou přidružené ke knihovně čas standardu ANSI, který je deklarován v čase. H.

- Podpora pro systémové hodiny. S knihovnou MFC verze 3.0, přidala se podpora pro `CTime` pro Win32 `SYSTEMTIME` a `FILETIME` datové typy.

- Podpora pro automatizaci [DATE – datový typ](../atl-mfc-shared/date-type.md). Datum podporuje datum, čas a hodnoty data a času. [COleDateTime](../atl-mfc-shared/reference/coledatetime-class.md) a [coledatetimespan –](../atl-mfc-shared/reference/coledatetimespan-class.md) zapouzdřují tuto funkci. Při práci s [COleVariant](../mfc/reference/colevariant-class.md) pomocí podporu automatizace.

## <a name="what-do-you-want-to-know-more-about"></a>Co chcete zjistit více informací

- [Datum a čas: Podpora SYSTEMTIME](../atl-mfc-shared/date-and-time-systemtime-support.md)

- [Datum a čas: Podpora automatizace](../atl-mfc-shared/date-and-time-automation-support.md)

- [Datum a čas: Podpora databáze](../atl-mfc-shared/date-and-time-database-support.md)

## <a name="see-also"></a>Viz také

[Koncepty](../mfc/mfc-concepts.md)   
[Obecná témata MFC](../mfc/general-mfc-topics.md)

