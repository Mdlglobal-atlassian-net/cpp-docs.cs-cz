---
title: Změna symbolu nebo názvu symbolu (ID) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.symbol.changing
dev_langs:
- C++
helpviewer_keywords:
- symbol names
- symbols [C++], names
ms.assetid: 26541832-8dba-4177-b642-e08f94502ea7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 8b80c854d144f0f2010d1482a03f692062ea81ef
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2018
ms.locfileid: "44315896"
---
# <a name="changing-a-symbol-or-symbol-name-id"></a>Změna symbolu nebo názvu symbolu (ID)

Při vytváření nového prostředku nebo prostředku objektu vývojové prostředí jí přiřadí výchozí název symbolu, například IDD_DIALOG1. Můžete použít [okno vlastností](/visualstudio/ide/reference/properties-window) Chcete-li změnit výchozí název symbolu nebo chcete změnit název žádný symbol už přidružené k prostředku.

### <a name="to-change-a-resources-symbol-name"></a>Chcete-li změnit název symbolu prostředku

1. V [zobrazení prostředků](../windows/resource-view-window.md), vyberte prostředek.

   > [!NOTE]
   > Pokud váš projekt již neobsahuje soubor .rc, najdete [vytváření nového souboru skriptu prostředků](../windows/how-to-create-a-resource-script-file.md).

2. V **vlastnosti** okno, zadejte nový název symbolu nebo vyberte ze seznamu existující symboly v **ID** pole.

   Pokud zadáte nový název symbolu, je automaticky přiřazena hodnota.

Můžete použít [symboly prostředků – dialogové okno](../windows/resource-symbols-dialog-box.md) změnit názvy symbolů není aktuálně přiřazená k prostředku. Další informace najdete v tématu [změna nepřiřazených symbolů](../windows/changing-unassigned-symbols.md).

## <a name="requirements"></a>Požadavky

Win32

## <a name="see-also"></a>Viz také

[Omezení názvu symbolu](../windows/symbol-name-restrictions.md)  
[ID předdefinovaných symbolů](../windows/predefined-symbol-ids.md)