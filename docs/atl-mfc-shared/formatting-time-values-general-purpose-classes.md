---
title: 'Formátování časových hodnot: Obecné třídy'
ms.date: 11/04/2016
helpviewer_keywords:
- dates, calculating intervals
- elapsed time, string representation
- time [C++], formatting
- formatting [C++], time
ms.assetid: 7fcfee24-f874-4a4d-95b3-adc19a0f2df0
ms.openlocfilehash: 48290adbc3e0e7f3cbe9a5a8e0569a5b61833e8c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50478660"
---
# <a name="formatting-time-values-general-purpose-classes"></a>Formátování časových hodnot: Obecné třídy

Následující postup ukazuje, jak formátuje hodnoty času.

#### <a name="to-format-a-string-representation-of-a-time-or-elapsed-time"></a>K formátování řetězcovou reprezentaci čas nebo uplynulý čas

Použití `Format` členskou funkci ze buď [CTime](../atl-mfc-shared/reference/ctime-class.md) nebo [ctimespan –](../atl-mfc-shared/reference/ctimespan-class.md) třídy k vytvoření znak řetězcové vyjádření čas nebo uplynulého času, jak je znázorněno v následujícím příkladu.

   [!code-cpp[NVC_ATLMFC_Utilities#175](../atl-mfc-shared/codesnippet/cpp/formatting-time-values-general-purpose-classes_1.cpp)]

## <a name="what-do-you-want-to-know-more-about"></a>Co chcete zjistit více informací

- [Obecné datum a čas programování v prostředí MFC](../atl-mfc-shared/date-and-time.md)

- [Práce s SYSTEMTIME](../atl-mfc-shared/date-and-time-systemtime-support.md)

- [Podpora automatizace data a času programování](../atl-mfc-shared/date-and-time-automation-support.md)

