---
title: 'Aktuální čas: Třídy pro obecné účely | Microsoft Docs'
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
ms.openlocfilehash: ec71cf76f859457aa76e69b57b58db3940e974da
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32354592"
---
# <a name="current-time-general-purpose-classes"></a>Aktuální čas: Třídy pro obecné účely
Následující postup ukazuje, jak vytvořit `CTime` objektu a provést jeho inicializaci s aktuálním časem.  
  
#### <a name="to-get-the-current-time"></a>Chcete-li získat aktuální čas  
  
1.  Přidělit `CTime` objektu následujícím způsobem:  
  
     [!code-cpp[NVC_ATLMFC_Utilities#171](../atl-mfc-shared/codesnippet/cpp/current-time-general-purpose-classes_1.cpp)]  
  
    > [!NOTE]
    >  Neinicializovaný `CTime` objekty nejsou inicializovány na platný čas.  
  
2.  Volání `CTime::GetCurrentTime` funkce získat aktuální čas z operačního systému. Funkce vrátí hodnotu `CTime` objekt, který slouží k nastavení hodnoty `CTime`, a to takto:  
  
     [!code-cpp[NVC_ATLMFC_Utilities#172](../atl-mfc-shared/codesnippet/cpp/current-time-general-purpose-classes_2.cpp)]  
  
     Vzhledem k tomu `GetCurrentTime` je funkce statický člen z `CTime` třídy, musíte v stejný název jako název třídy a operátor řešení rozsahu (`::`), `CTime::GetCurrentTime()`.  
  
 Samozřejmě dva kroky popsané dříve může zkombinovat do jednoho příkazu program následujícím způsobem:  
  
 [!code-cpp[NVC_ATLMFC_Utilities#173](../atl-mfc-shared/codesnippet/cpp/current-time-general-purpose-classes_3.cpp)]  
  
## <a name="see-also"></a>Viz také  
 [Datum a čas: Obecné třídy](../atl-mfc-shared/date-and-time-general-purpose-classes.md)



