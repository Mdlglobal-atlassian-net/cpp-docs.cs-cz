---
title: Vytváření nemodálních dialogových oken
ms.date: 11/04/2016
helpviewer_keywords:
- MFC dialog boxes [MFC], modeless
- modeless dialog boxes [MFC], creating
- MFC dialog boxes [MFC], creating
ms.assetid: 70d78c7f-3d40-477b-9f78-0f33c359f88b
ms.openlocfilehash: 7da6d82257d1407dfcf4d6d3c15cdadbb8c0fa30
ms.sourcegitcommit: 1e6386be9084f70def7b3b8b4bab319a117102b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/30/2019
ms.locfileid: "71685667"
---
# <a name="creating-modeless-dialog-boxes"></a>Vytváření nemodálních dialogových oken

V případě nemodálního dialogového okna musíte zadat vlastní veřejný konstruktor ve třídě dialogového okna. Chcete-li vytvořit nemodální dialogové okno, zavolejte svůj veřejný konstruktor a potom zavolejte funkci [Create](../mfc/reference/cdialog-class.md#create) member objektu dialogového okna pro načtení prostředku dialogového okna. Můžete volat **Create** buď během, nebo po volání konstruktoru. Pokud má prostředek dialogového okna vlastnost **WS_VISIBLE**, zobrazí se dialogové okno hned. V takovém případě je nutné zavolat jeho členskou funkci [: ShowWindow](../mfc/reference/cwnd-class.md#showwindow) .

## <a name="see-also"></a>Další informace najdete v tématech

[Práce s dialogovými okny v MFC](../mfc/life-cycle-of-a-dialog-box.md)
