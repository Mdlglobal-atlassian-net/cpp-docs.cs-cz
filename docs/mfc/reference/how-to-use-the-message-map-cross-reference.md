---
title: 'Postupy: použití křížových odkazů mapování zpráv | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.mfc.messages
dev_langs:
- C++
helpviewer_keywords:
- windows [MFC], message maps
ms.assetid: 2e863d23-9e58-45ba-b5e4-a8ceefccd0c8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fccdf620cbdaeffc7fb201e014edc4c7c1dddc83
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46434450"
---
# <a name="how-to-use-the-message-map-cross-reference"></a>Postupy: Použití křížových odkazů mapování zpráv

V položkách s popiskem \<memberFxn >, psát členské funkce pro odvozený [CWnd](../../mfc/reference/cwnd-class.md) třídy. Pojmenujte svoji funkci všechny, který rádi používáte. Ostatní funkce, jako například `OnActivate`, jsou členské funkce třídy `CWnd`. Pokud je volána, předají zpráva, která má `DefWindowProc` funkce Windows. Ke zpracování zpráv s oznámením Windows, přepište odpovídající `CWnd` funkce v odvozené třídě. Funkce by měly volat přepsané funkce v základní třídu umožňuje základní třídy a Windows reagují na zprávy.

Ve všech případech se umístit do prototypu funkce `CWnd`-odvozené třídy záhlaví a kód položku mapování zpráv, jak je znázorněno.

Se používají následující termíny:

|Termín|Definice|
|----------|----------------|
|id|ID položky nabídky definovaný uživatelem (wm_command – zprávy) nebo ID ovládacího prvku (zprávy v podřízených oknech oznámení).|
|"zpráva" a "funkci wNotifyCode"|Windows ID zprávy, jak je definováno v systému WINDOWS. H.|
|nMessageVariable|Název proměnné, která obsahuje návratovou hodnotu z `RegisterWindowMessage` funkce Windows.|

## <a name="see-also"></a>Viz také

[Mapy zpráv](../../mfc/reference/message-maps-mfc.md)

