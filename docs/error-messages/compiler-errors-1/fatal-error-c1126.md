---
title: Závažná chyba C1126
ms.date: 11/04/2016
f1_keywords:
- C1126
helpviewer_keywords:
- C1126
ms.assetid: f22b26a6-8ad7-47cf-a237-196c8ea60aca
ms.openlocfilehash: a6c9d06cd087eb4462ae475cc1f6d64ba451887f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80203628"
---
# <a name="fatal-error-c1126"></a>Závažná chyba C1126

' identifier ': Automatická alokace překračuje velikost

Místo přidělené pro lokální proměnné funkce (plus omezené množství místa, které kompilátor používá, jako je například dalších 20 bajtů pro vyměnitelné funkce) překračuje limit.

Chcete-li tuto chybu opravit, použijte `malloc` nebo `new` k přidělení velkých objemů dat.
