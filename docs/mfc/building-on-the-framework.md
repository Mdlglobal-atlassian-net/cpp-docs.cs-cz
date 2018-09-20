---
title: Sestavení v rámci | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- application-specific classes [MFC]
- application framework [MFC], building applications
- applications [MFC]
- MFC, application development
ms.assetid: 883f0f19-866f-4221-8a3d-5607941dc8d0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4ca0ebd9bf03df8725c14df8d2aca1f7858b7b65
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46396178"
---
# <a name="building-on-the-framework"></a>Sestavení na základě rozhraní .NET Framework

Je vaše role při konfiguraci aplikace s použitím rozhraní MFC framework slouží k poskytování specifické pro aplikaci zdrojový kód a pro připojení k součásti tak, že definujete, jaké zprávy a příkazy, na které reagují. Pomocí jazyka C++ a standardní C++ techniky k odvození třídy specifické pro aplikaci od těch, které poskytl knihovny tříd a přepsat a rozšiřují chování základní třídy.

Následující tabulky popisují v souvisejících tématech obecného operace, které se obvykle provedením a vaše odpovědnosti a povinnosti v rámci:

- [Pořadí pro vytvoření aplikace s použitím rozhraní Framework](../mfc/sequence-of-operations-for-building-mfc-applications.md)

- [Posloupnost operací při vytváření aplikací OLE](../mfc/sequence-of-operations-for-creating-ole-applications.md)

- [Posloupnost operací při vytváření ovládacích prvků ActiveX](../mfc/sequence-of-operations-for-creating-activex-controls.md)

- [Posloupnost operací při vytváření databázových aplikací](../mfc/sequence-of-operations-for-creating-database-applications.md)

Ve většině případů můžete postupovat podle těchto tabulek jako řadu kroků pro vytvoření aplikace knihovny MFC, i když některé z kroků alternativní způsoby. Například většina aplikací používá jeden typ třídy zobrazení z několika typů, které jsou k dispozici.

## <a name="see-also"></a>Viz také

[Obecná témata MFC](../mfc/general-mfc-topics.md)

