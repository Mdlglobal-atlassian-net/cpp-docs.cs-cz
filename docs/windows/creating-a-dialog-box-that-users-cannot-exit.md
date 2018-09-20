---
title: Vytváření dialogové okno (C++), které uživatelé nemohou zavřít. | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- dialog boxes [C++], creating
- modal dialog boxes [C++], logon screens
- logon screens
ms.assetid: 54823c27-1658-4388-bd12-0a1ce8f3899e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 5abae461b4298d8a6300f5d7ad9f3e162a5b21c8
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46447385"
---
# <a name="creating-a-dialog-box-c-that-users-cannot-exit"></a>Vytvoření dialogového okna (C++), které uživatelé nemohou zavřít.

Můžete vytvořit modul runtime dialogové okno, které uživatel nemůže ukončeno. Tento druh dialogové okno je užitečný pro přihlášení a pro aplikace nebo dokumentu zámky.

### <a name="to-create-a-dialog-box-that-a-user-cannot-exit"></a>Chcete-li vytvořit dialogové okno, které uživatel nemohou zavřít.

1. V **vlastnosti** podokno pro dialogové okno, nastavte **systémové nabídky** vlastnost **false**.

   Zakáže nabídky systému dialogového a **Zavřít** tlačítko.

2. V dialogovém okně pole formuláře, odstraňte **zrušit** a **OK** tlačítka.

   V době běhu nemůže uživatel ukončit modální dialogové okno, které má tyto vlastnosti.

Pokud chcete povolit testování tohoto druhu dialogového okna, test dialog box – funkce zjistí při **Esc** stisknutí. (**Esc** se také označuje jako virtuální vk_escape – klíč.) Bez ohledu na to, jak je určen dialogovém okně chování za běhu, můžete ukončit ji v režimu testu stisknutím kombinace kláves **Esc**.

> [!NOTE]
> Pro aplikace knihovny MFC, chcete-li vytvořit dialogové okno, které uživatelé nebudou moct zavřít, je nutné přepsat výchozí chování `OnOK` a `OnCancel` vzhledem k tomu, že i v případě, že odstraníte přidružené tlačítka, dialogové okno může stále vynechat stisknutím klávesy  **Zadejte** nebo **Esc**.

Informace o tom, jak přidat prostředky do spravovaných projektů naleznete v tématu [prostředky v desktopových aplikací](/dotnet/framework/resources/index).

## <a name="requirements"></a>Požadavky

Win32

## <a name="see-also"></a>Viz také

[Postupy: Vytvoření prostředku](../windows/how-to-create-a-resource.md)<br/>
[Soubory prostředků](../windows/resource-files-visual-studio.md)<br/>
[Editor dialogových oken](../windows/dialog-editor.md)