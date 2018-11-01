---
title: Vlastnost typu akcelerátoru (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- Type property
- VIRTKEY
ms.assetid: 8c349bc4-e6ad-43fa-959e-f29168af35b8
ms.openlocfilehash: 00699f31b821aa508feec9ffe062d768f27ee5a2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50475582"
---
# <a name="accelerator-type-property-c"></a>Vlastnost typu akcelerátoru (C++)

Akcelerátor **typ** vlastnost určuje, zda kombinaci kláves přidružené k ID akcelerátoru je virtuální kombinace kláves nebo klíče hodnota ASCII a ANSI:

- Pokud **typ** ASCII, je vlastnost [modifikátor](../windows/accelerator-modifier-property.md) můžou být jenom `None` nebo `Alt`, nebo může mít akcelerátor, který používá **Ctrl** (určeného klíče klíč s předchozím `^`).

- Pokud **typ** vlastnost je VIRTKEY libovolnou kombinaci `Modifier` a `Key` hodnoty je platný.

   > [!NOTE]
   > Pokud chcete zadat hodnotu do tabulky akcelerátorů a mají hodnotu považovat za ASCII a ANSI, jednoduše klikněte na tlačítko **typ** pro položku v tabulce a z rozevíracího seznamu vyberte ASCII. Ale pokud použijete **další stisknutá klávesa** příkazu (**upravit** nabídky) k určení `Key`, musíte změnit **typ** vlastnost z VIRTKEY ASCII *před* zadávání `Key` kódu.

## <a name="requirements"></a>Požadavky

Win32

## <a name="see-also"></a>Viz také

[Nastavení vlastností akcelerátoru](../windows/setting-accelerator-properties.md)<br/>
[Editor akcelerátorů](../windows/accelerator-editor.md)