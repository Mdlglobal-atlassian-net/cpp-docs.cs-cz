---
title: Standardní identifikátory příkazů a oken
ms.date: 11/04/2016
helpviewer_keywords:
- standard command and Window IDs
ms.assetid: 0424805c-fff8-4531-8f0c-15cfb13aa612
ms.openlocfilehash: 40783bc19e51afb0e9fe9e4a429df0239a8e7f09
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/11/2019
ms.locfileid: "70907719"
---
# <a name="standard-command-and-window-ids"></a>Standardní identifikátory příkazů a oken

Knihovna Microsoft Foundation Class definuje počet standardních ID příkazů a oken v AFXRES. h. Tato ID se nejčastěji používají v editorech prostředků a v [Průvodci třídou](mfc-class-wizard.md) pro mapování zpráv na funkce obslužných rutin. Všechny standardní příkazy mají předponu **ID_** . Například když použijete Editor nabídek, normálně navážete položku nabídky otevření souboru na standardní ID příkazu ID_FILE_OPEN.

U většiny standardních příkazů není nutné, aby kód aplikace odkazoval na ID příkazu, protože samotné rozhraní zpracovává příkazy prostřednictvím`CWinThread`map zpráv v primárních třídách rozhraní (, `CWinApp`, `CView` `CDocument`, a tak dále).

Kromě standardních ID příkazů je definováno několik dalších identifikátorů Standard, které mají předponu **AFX_ID**. Tato ID zahrnují standardní ID oken (prefix **AFX_IDW_** ), ID řetězců (předpona **AFX_IDS_** ) a několik dalších typů.

Identifikátory začínající předponou **AFX_ID** jsou často používány programátory, ale při přepsání funkcí rozhraní, které také odkazují na **AFX_ID**, může být nutné, abyste na tyto identifikátory odkazovali.

V tomto odkazu nejsou zdokumentovány jednotlivě. Další informace o nich najdete v technické poznámky [20](../../mfc/tn020-id-naming-and-numbering-conventions.md), [21](../../mfc/tn021-command-and-message-routing.md)a [22](../../mfc/tn022-standard-commands-implementation.md).

> [!NOTE]
>  Hlavičkový soubor AFXRES. h je nepřímo zahrnutý v afxwin. h. Do souboru skriptu prostředků vaší aplikace (. RC) musíte explicitně zahrnout následující příkaz:

[!code-cpp[NVC_MFC_Utilities#47](../../mfc/codesnippet/cpp/standard-command-and-window-ids_1.h)]

## <a name="see-also"></a>Viz také:

[Makra a globální prvky](../../mfc/reference/mfc-macros-and-globals.md)
