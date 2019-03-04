---
title: Standardní identifikátory příkazů a oken
ms.date: 11/04/2016
f1_keywords:
- vc.mfc.macros
helpviewer_keywords:
- standard command and Window IDs
ms.assetid: 0424805c-fff8-4531-8f0c-15cfb13aa612
ms.openlocfilehash: e5f6955407f565d5cc06ef57e9bd273f6c0f7712
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57267248"
---
# <a name="standard-command-and-window-ids"></a>Standardní identifikátory příkazů a oken

Knihovny Microsoft Foundation Class definuje počet standardních příkazů a oken ID v souboru Afxres.h. Tyto identifikátory se nejčastěji používají v rámci editory prostředků nebo v okně Vlastnosti pro mapování zpráv na funkce obslužné rutiny. Všechny standardní příkazy mají **ID_** předponu. Například pokud používáte editor nabídek, obvykle svážete otevřít soubor položky nabídky standardní ID id_file_open – příkaz

Pro většinu standardních příkazů kód aplikace nepotřebuje k odkazování na ID příkazu, protože samotného rozhraní zpracovává příkazy prostřednictvím mapy zpráv v jeho primární rozhraní tříd (`CWinThread`, `CWinApp`, `CView`, `CDocument`, a tak dále).

Kromě identifikátory standardních příkazů, jsou definovány počet dalších standardních ID, které mají předponu z **AFX_ID**. Tyto identifikátory zahrnují standardní okno ID (předpona **AFX_IDW_**), řetězec ID (předpona **AFX_IDS_**) a několik dalších typů.

ID, které začínají **AFX_ID** předpony jsou zřídka používané programátory, ale můžete potřebovat k odkazování na tyto identifikátory při přepisování funkce rozhraní framework, které také odkazovat **AFX_ID**s.

ID nejsou jednotlivě uvedené v tomto odkazu. Další informace o nich najdete v technické poznámky [20](../../mfc/tn020-id-naming-and-numbering-conventions.md), [21](../../mfc/tn021-command-and-message-routing.md), a [22](../../mfc/tn022-standard-commands-implementation.md).

> [!NOTE]
>  Hlavička souboru Afxres.h je nepřímo součástí Afxwin.h. V souboru skriptu (.rc) prostředků vaší aplikace musí explicitně zahrnovat následující příkaz:

[!code-cpp[NVC_MFC_Utilities#47](../../mfc/codesnippet/cpp/standard-command-and-window-ids_1.h)]

## <a name="see-also"></a>Viz také:

[Makra a globální prvky](../../mfc/reference/mfc-macros-and-globals.md)
