---
title: Vlastnost typu akcelerátoru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Type property
- VIRTKEY
ms.assetid: 8c349bc4-e6ad-43fa-959e-f29168af35b8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 59fae6d0809e32883d5d56e43e64525e23643d91
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42602323"
---
# <a name="accelerator-type-property"></a>Vlastnost typu akcelerátoru

Akcelerátor **typ** vlastnost určuje, zda kombinaci kláves přidružené k ID akcelerátoru je virtuální kombinace kláves nebo klíče hodnota ASCII a ANSI:

- Pokud **typ** ASCII, je vlastnost [modifikátor](../windows/accelerator-modifier-property.md) můžou být jenom `None` nebo `Alt`, nebo může mít akcelerátor, který používá **Ctrl** (určeného klíče klíč s předchozím `^`).

- Pokud **typ** vlastnost je VIRTKEY libovolnou kombinaci `Modifier` a `Key` hodnoty je platný.

   > [!NOTE]
   > Pokud chcete zadat hodnotu do tabulky akcelerátorů a mají hodnotu považovat za ASCII a ANSI, jednoduše klikněte na tlačítko **typ** pro položku v tabulce a z rozevíracího seznamu vyberte ASCII. Ale pokud použijete **další stisknutá klávesa** příkazu (**upravit** nabídky) k určení `Key`, musíte změnit **typ** vlastnost z VIRTKEY ASCII *před* zadávání `Key` kódu.

## <a name="requirements"></a>Požadavky

Win32

## <a name="see-also"></a>Viz také

[Nastavení vlastností akcelerátoru](../windows/setting-accelerator-properties.md)  
[Editor akcelerátorů](../windows/accelerator-editor.md)