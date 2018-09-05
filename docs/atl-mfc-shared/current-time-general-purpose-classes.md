---
title: 'Aktuální čas: Obecné třídy | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- time, setting current
- current time, CTime object
- procedures, getting current time
- initializing objects, with the current time
- time, getting current
ms.assetid: c39e6775-6a92-4b27-95a7-5c86ed371d8a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fff4c581b91ed789b501d3866eb9b3b259a662b3
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43755460"
---
# <a name="current-time-general-purpose-classes"></a>Aktuální čas: Obecné třídy

Následující postup ukazuje, jak vytvořit `CTime` objektu a inicializovat s aktuálním časem.

#### <a name="to-get-the-current-time"></a>Chcete-li získat aktuální čas

1. Přidělit `CTime` objektu následujícím způsobem:

   [!code-cpp[NVC_ATLMFC_Utilities#171](../atl-mfc-shared/codesnippet/cpp/current-time-general-purpose-classes_1.cpp)]

   > [!NOTE]
   > Neinicializované `CTime` objekty nejsou inicializovány na platný čas.

2. Volání `CTime::GetCurrentTime` funkce získat aktuální čas v operačním systému. Tato funkce vrací `CTime` objekt, který slouží k nastavení hodnoty `CTime`, následujícím způsobem:

   [!code-cpp[NVC_ATLMFC_Utilities#172](../atl-mfc-shared/codesnippet/cpp/current-time-general-purpose-classes_2.cpp)]

   Protože `GetCurrentTime` je statickou členskou funkci ze `CTime` třídy, musí být stejný název jako název třídy a operátorem rozlišení oboru (`::`), `CTime::GetCurrentTime()`.

Samozřejmě dva kroky popsané dříve se dají zkombinovat do jednoho příkazu program následujícím způsobem:

[!code-cpp[NVC_ATLMFC_Utilities#173](../atl-mfc-shared/codesnippet/cpp/current-time-general-purpose-classes_3.cpp)]
