---
title: Standardní identifikátory příkazů a oken
ms.date: 11/04/2016
helpviewer_keywords:
- standard command and Window IDs
ms.assetid: 0424805c-fff8-4531-8f0c-15cfb13aa612
ms.openlocfilehash: a7f9e37702c686e13379d4034be94949f92e5e79
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372961"
---
# <a name="standard-command-and-window-ids"></a>Standardní identifikátory příkazů a oken

Knihovna tříd Microsoft Foundation definuje v souboru Afxres.h řadu standardních ID příkazů a oken. Tato ID se nejčastěji používají v editorech prostředků a [V Průvodci třídou](mfc-class-wizard.md) k mapování zpráv na funkce obslužné rutiny. Všechny standardní příkazy mají **předponu ID_.** Pokud například používáte editor nabídek, obvykle svážete položku nabídky Otevřít soubor se standardním ID příkazu ID_FILE_OPEN.

U většiny standardních příkazů nemusí kód aplikace odkazovat na ID příkazu, protože samotné rozhraní zpracovává příkazy`CWinThread` `CWinApp`prostřednictvím map zpráv v primárních třídách rozhraní ( , , `CView`, `CDocument`, a tak dále).

Kromě standardních ID příkazů je definována řada dalších standardních ID, která mají předponu **AFX_ID**. Tato ID zahrnují standardní ID oken (předponu **AFX_IDW_),** ID řetězce (předponu **AFX_IDS_**) a několik dalších typů.

ID, které začínají **předponou AFX_ID** jsou zřídka používány programátory, ale možná budete muset odkazovat na tyto ID při přepsání funkce rozhraní, které také odkazují na **AFX_ID**s.

ID nejsou v tomto odkazu jednotlivě zdokumentována. Více informací o nich naleznete v technických poznámkách [20](../../mfc/tn020-id-naming-and-numbering-conventions.md), [21](../../mfc/tn021-command-and-message-routing.md)a [22](../../mfc/tn022-standard-commands-implementation.md).

> [!NOTE]
> Hlavičkový soubor Afxres.h je nepřímo součástí souboru Afxwin.h. Do souboru skriptu prostředků aplikace (.rc) je nutné explicitně zahrnout následující příkaz:

[!code-cpp[NVC_MFC_Utilities#47](../../mfc/codesnippet/cpp/standard-command-and-window-ids_1.h)]

## <a name="see-also"></a>Viz také

[Makra a globální](../../mfc/reference/mfc-macros-and-globals.md)
