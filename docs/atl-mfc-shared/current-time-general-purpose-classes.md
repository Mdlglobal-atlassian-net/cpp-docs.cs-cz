---
title: "Aktuální čas: Třídy pro obecné účely | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: C++
helpviewer_keywords:
- time, setting current
- current time, CTime object
- procedures, getting current time
- initializing objects, with the current time
- time, getting current
ms.assetid: c39e6775-6a92-4b27-95a7-5c86ed371d8a
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: d40f0044795c6fd7c5df3850261ceb4314f50dbd
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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



