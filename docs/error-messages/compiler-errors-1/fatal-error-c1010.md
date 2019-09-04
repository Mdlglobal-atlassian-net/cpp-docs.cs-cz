---
title: Závažná chyba C1010
ms.date: 09/03/2019
f1_keywords:
- C1010
helpviewer_keywords:
- C1010
ms.assetid: dfd035f1-a7a2-40bc-bc92-dc4d7f456767
ms.openlocfilehash: 0315af63e9fdbbb0b136a85a23cb28936dee6836
ms.sourcegitcommit: fd0f8839da5c6a3663798a47c6b0bb6e63b518bd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70273564"
---
# <a name="fatal-error-c1010"></a>Závažná chyba C1010

> při hledání předkompilované hlavičky byl zjištěn neočekávaný konec souboru. Nezapomněli jste do zdroje přidat *název*#include?

## <a name="remarks"></a>Poznámky

Soubor zahrnutí určený parametrem [/Yu](../../build/reference/yu-use-precompiled-header-file.md) není uveden ve zdrojovém souboru. Tato možnost je ve výchozím nastavení povolena v mnoha typech C++ projektů aplikace Visual Studio. Výchozí soubor zahrnutí určený touto možností je *PCH. h*nebo *stdafx. h* v aplikaci Visual Studio 2017 a starší.

V prostředí sady Visual Studio použijte k vyřešení této chyby jednu z následujících metod:

- Ujistěte se, že jste nechtěně neodstranili, přejmenovali nebo odebrali soubor hlaviček *PCH. h* nebo zdrojový soubor *PCH. cpp* z aktuálního projektu. (Ve starších projektech mohou být tyto soubory pojmenovány *stdafx. h* a *stdafx. cpp*.)

- Zajistěte, aby byl soubor hlaviček *PCH. h* nebo *stdafx. h* zahrnut před jakýmkoli jiným kódem nebo direktivami preprocesoru ve zdrojových souborech. (V aplikaci Visual Studio je tento hlavičkový soubor určen vlastností **souboru předkompilované hlavičky** .)

- Můžete vypnout použití předkompilovaných hlaviček. Pokud vypnete předkompilované hlavičky, může mít vážně vliv na výkon sestavení.

### <a name="to-turn-off-precompiled-headers"></a>Vypnutí předkompilovaných hlaviček

Chcete-li vypnout použití předkompilovaných hlaviček v projektu, použijte následující postup:

1. V okně **Průzkumník řešení** klikněte pravým tlačítkem myši na název projektu a pak zvolte **vlastnosti** . tím otevřete dialogové okno **stránky vlastností** projektu.

1. V rozevíracím seznamu **Konfigurace** vyberte možnost **všechny konfigurace**.

1. Vyberte stránku vlastností **vlastnosti** > konfigurace**CC++/**  > **Předkompilovaná hlavička** .

1. V seznamu vlastností vyberte rozevírací nabídku pro vlastnost **předkompilované hlavičky** a pak zvolte možnost **Nepoužívat předkompilované hlavičky**. Kliknutím na **tlačítko OK** uložte změny.

1. V okně **Průzkumník řešení** klikněte pravým tlačítkem na zdrojový soubor *PCH. cpp* v projektu. (Ve starších projektech soubor může mít název *stdafx. cpp*.) Chcete-li odebrat ze sestavení, vyberte možnost **vyloučit z projektu** .

1. K odstranění všech souborů *PROJECT_NAME. pch* v zprostředkujících adresářích sestavení použijte příkaz nabídky **sestavit** > **Vyčištění řešení** pro každou vámi sestavenou konfiguraci.

## <a name="see-also"></a>Viz také:

[Předkompilované hlavičkové soubory](../../build/creating-precompiled-header-files.md)\
[/YC (Vytvořit předkompilovaný hlavičkový soubor)](../../build/reference/yc-create-precompiled-header-file.md)\
[/Yu (použít předkompilovaný hlavičkový soubor)](../../build/reference/yu-use-precompiled-header-file.md)