---
title: 'Postupy: otevření souboru skriptu prostředků mimo projekt jazyka C++ (samostatně) | Dokumentace Microsoftu'
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
- resources [C++], viewing
- rc files [C++], viewing resources
- .rc files [C++], viewing resources
- resource script files [C++], viewing resources
ms.assetid: bc350c60-178d-4c5d-9a7e-6576b0c936e4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 1e52d78de0026fa4a589877ee0a591da26107fde
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46391530"
---
# <a name="how-to-open-a-resource-script-file-outside-of-a-c-project-standalone"></a>Postupy: otevření souboru skriptu prostředků mimo projekt jazyka C++ (samostatný)

Prostředky můžete zobrazit v souboru .rc bez nutnosti otevřít projekt. Otevře se v okně dokumentu na rozdíl od otevřít v souboru .rc [zobrazení prostředků](../windows/resource-view-window.md) okno (stejně jako když je soubor otevřen, uvnitř projektu).

> [!NOTE]
> Jde o důležité odlišení, protože některé příkazy nejsou k dispozici, pouze když je soubor otevřen samostatné (mimo projekt). Například můžete pouze uložení souboru do jiného formátu nebo jako jiný název souboru při otevření souboru mimo projekt ( **uložit jako** příkazu není dostupná, když je soubor otevřen v projektu).

### <a name="to-open-an-rc-file-outside-a-project"></a>Otevřete soubor .rc mimo projekt

1. Z **souboru** nabídce zvolte **otevřít**, klikněte na **souboru**.

2. V **otevřít soubor** dialogové okno, přejděte do souboru skriptu prostředků, kterou chcete zobrazit, zvýrazněte ho a klikněte na **otevřít**.

   > [!NOTE]
   > Pokud nejprve otevřete projekt (**souboru**, **otevřete**, **projektu**), nebudou mít k dispozici některé příkazy. Otevřít soubor "standalone" znamená otevření bez první načtení projektu.

Otevřete a zobrazte soubor prostředků v textovém formátu, naleznete v tématu [úpravy skriptu prostředků (.rc) soubor](../windows/how-to-open-a-resource-script-file-in-text-format.md).

### <a name="to-open-multiple-rc-files-outside-a-project"></a>K otevření více souborů .rc mimo projekt

1. Otevřete oba samostatné soubory prostředků. Například otevřete `Source1.rc` a `Source2.rc`.

   1. Z **souboru** nabídce zvolte **otevřít**, klikněte na **souboru**.

   2. V **otevřít soubor** dialogové okno, přejděte do první souboru skriptu prostředků, kterou chcete otevřít (`Source1.rc`), zvýrazněte ho a klikněte na tlačítko **otevřete**.

   3. Opakujte předchozí krok pro druhý .rc soubor otevřít (`Source2.rc`).

       Soubory .rc jsou teď otevřít v systému windows v samostatných dokumentech.

2. Když jsou otevřené oba soubory .rc, dlaždici windows, takže je možné současně zobrazit:

   - Z **okno** nabídce zvolte **Nová vodorovná skupina karet** nebo **Nová svislá skupina karet**.

       \- nebo –

   - Klikněte pravým tlačítkem na jeden ze souborů .rc a zvolte **Nová vodorovná skupina karet** nebo **Nová svislá skupina karet** z místní nabídky.

> [!NOTE]
> Pokud váš projekt již neobsahuje soubor .rc, najdete [vytváření nového souboru skriptu prostředků](../windows/how-to-create-a-resource-script-file.md).

## <a name="requirements"></a>Požadavky

Win32

## <a name="see-also"></a>Viz také

[Soubory prostředků](../windows/resource-files-visual-studio.md)<br/>
[Editory prostředků](../windows/resource-editors.md)