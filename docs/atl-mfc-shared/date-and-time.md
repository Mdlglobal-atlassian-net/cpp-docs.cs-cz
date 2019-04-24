---
title: Datum a čas
ms.date: 11/04/2016
helpviewer_keywords:
- time, MFC programming
- time
- MFC, date and time
- dates, MFC
ms.assetid: ecf56dc5-d418-4603-ad3e-af7e205a6403
ms.openlocfilehash: 32222b4a2a529716db2c414e0281e1b1ba16a0dd
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62236421"
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

## <a name="see-also"></a>Viz také:

[Koncepty](../mfc/mfc-concepts.md)<br/>
[Obecná témata MFC](../mfc/general-mfc-topics.md)
