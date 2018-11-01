---
title: Náhled prostředků (C++)
ms.date: 11/04/2016
f1_keywords:
- vc.resvw.resource.previewing
- vs.resvw.resource.previewing
helpviewer_keywords:
- resources [C++], viewing
ms.assetid: d6abda66-0e2b-4ac3-a59a-a57b8c6fb70b
ms.openlocfilehash: 79756bd71dfc731b78b21bd4df311e4848beb899
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50589544"
---
# <a name="previewing-resources"></a>Náhled prostředků

Náhled prostředků vám umožní zobrazit grafických prostředků bez jejich otevírání. V předběžné verzi je také užitečné pro spustitelné soubory, poté, co jste je zkompilovat, protože identifikátory prostředků změnit na čísla. Protože tyto identifikátory číselné často neposkytuje dostatek informací, zobrazení náhledu prostředky vám pomůže rychle identifikovat.

Rozložení vizuálu z těchto typů prostředků můžete zobrazit náhled:

- Rastrový obrázek

- Dialogové okno

- Ikona

- Nabídka

- Kurzor

- Panel nástrojů

Funkce visual ve verzi preview se nevztahuje na akcelerátoru, Manifest, tabulka řetězců a informace o verzi zdroje.

### <a name="to-preview-resources"></a>Náhled prostředků

1. V [zobrazení prostředků](../windows/resource-view-window.md) nebo okno dokumentu, vyberte prostředek, třeba **IDD_ABOUTBOX**.

   > [!NOTE]
   > Pokud váš projekt již neobsahuje soubor .rc, najdete [vytváření nového souboru skriptu prostředků](../windows/how-to-create-a-resource-script-file.md).

2. V [okno vlastností](/visualstudio/ide/reference/properties-window), klikněte na tlačítko **stránky vlastností** tlačítko.

   \- nebo –

3. Na **zobrazení** nabídky, klikněte na tlačítko **stránky vlastností**.

   **Stránku vlastností** prostředek se otevře zobrazení ve verzi preview tohoto prostředku. Pak můžete použít **nahoru** a **dolů** v ovládacím prvku klávesy se šipkami přejdete strom **zobrazení prostředků** nebo okno dokumentu. **Stránku vlastností** zůstávají otevřené, který se zobrazí jakémukoli prostředku, který má právě fokus a může být zobrazen.

Informace o přidávání prostředků do spravovaných projektů, najdete v tématu [prostředky v desktopových aplikací](/dotnet/framework/resources/index) v *rozhraní .NET Framework Developer's Guide*. Informace o ručním přidání souborů prostředků do spravovaných projektů, přístupu k prostředkům, zobrazení statických prostředků a přiřazení řetězců prostředků k vlastnostem, naleznete v tématu [Creating Resource Files pro desktopových aplikací](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Informace o globalizace a lokalizace prostředků do spravovaných aplikací najdete v tématu [Globalizing a lokalizace aplikací .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Požadavky

Win32

## <a name="see-also"></a>Viz také

[Postupy: Otevření souboru skriptu prostředků mimo projekt (samostatný)](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md)<br/>
[Editory prostředků](../windows/resource-editors.md)