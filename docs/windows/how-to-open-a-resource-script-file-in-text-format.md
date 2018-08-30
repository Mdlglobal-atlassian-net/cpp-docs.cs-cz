---
title: 'Postupy: otevření souboru skriptu prostředků v textovém formátu | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.resource
dev_langs:
- C++
helpviewer_keywords:
- resource script files, opening in text format
- .rc files, opening in text format
- rc files, opening in text format
ms.assetid: 0bc57527-f53b-40c9-99a9-4dcbc5c9af57
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: aae516aeecd90a46544d1e9e28e1352fc73f6e2c
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43221457"
---
# <a name="how-to-open-a-resource-script-file-in-text-format"></a>Postupy: Otevření souboru skriptu prostředků v textovém formátu

Může nastat situace, kdy budete chtít zobrazit obsah souboru projektu prostředků skriptů (.rc) bez nutnosti otevřít prostředek, jako je například dialogové okno, v jeho editoru konkrétní prostředek. Můžete například hledání řetězce napříč všechna dialogová okna v souboru prostředků, aniž byste museli otevřít každý z nich samostatně.

> [!NOTE]
> Pokud váš projekt již neobsahuje soubor .rc, najdete [vytváření nového souboru skriptu prostředků](../windows/how-to-create-a-resource-script-file.md).

Snadno můžete otevřít soubor prostředků v textovém formátu k zobrazení všech prostředků, které obsahuje a globální operacích podporován [textový editor](https://msdn.microsoft.com/508e1f18-99d5-48ad-b5ad-d011b21c6ab1).

> [!NOTE]
> Editory prostředků nečtou přímo .rc nebo `resource.h` soubory. Nástroj resource compiler jejich kompiluje do soubory .aps, které se spotřebovávají editory prostředků. Tento soubor je kompilační krok a ukládá pouze datový symbolické. Jako normální zkompilovat procesu, se zahodí informace, které nejsou symbolické (například komentáře) v průběhu kompilace. Pokaždé, když se soubor .aps získá synchronizována se soubor .rc, se znovu vygeneroval soubor .rc (například když uložíte, editor prostředků přepíše soubor .rc a soubor resource.h). Všechny změny samotné prostředky zůstanou zahrnuté v souboru .rc, ale komentáře vždy ztratí dojde k přepsání souboru .rc. Informace o tom, jak zachovat komentáře, naleznete v tématu [včetně prostředků v době kompilace](../windows/how-to-include-resources-at-compile-time.md).

### <a name="to-open-a-resource-script-file-as-text"></a>K otevření souboru skriptu prostředků jako text

1. Z **souboru** nabídku zvolte **otevřít**, klikněte na **souboru.**

2. V **otevřít soubor** dialogové okno, přejděte do souboru skriptu prostředků, které chcete zobrazit v textovém formátu.

3. Zvýrazněte soubor a potom klikněte na šipku rozevíracího seznamu **otevřít** tlačítko (nachází se na pravé straně tlačítka).

4. Zvolte **otevřít v** z rozevírací nabídky.

5. V **otevřít v** dialogové okno, klikněte na tlačítko **Editor zdrojového kódu (textu)**.

6. Z **otevřít jako** rozevíracího seznamu vyberte **Text**.

   Prostředek se otevře v **zdrojový kód** editoru.

\- nebo –

1. V **Průzkumníka řešení**, klikněte pravým tlačítkem na soubor .rc.

2. V místní nabídce zvolte **otevřít v programu...** a pak vyberte **Editor zdrojového kódu (textu)**.

## <a name="requirements"></a>Požadavky

Win32

## <a name="see-also"></a>Viz také

[Soubory prostředků](../windows/resource-files-visual-studio.md)  
[Editory prostředků](../windows/resource-editors.md)