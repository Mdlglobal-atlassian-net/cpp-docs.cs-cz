---
title: Uživatelem definované nástroje | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- user-defined tools (MFC Extensions)
ms.assetid: cb887421-78ce-4652-bc67-96a53984ccaa
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a3b755fc35c98652ab87231e9d8f58cde748bfc0
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33384345"
---
# <a name="user-defined-tools"></a>Uživatelem definované nástroje
MFC podporuje uživatelem definované nástroje. Uživatelem definované nástroje je speciální příkaz, který spustí program externí, zadaného uživatelem. Přizpůsobení procesu můžete použít ke správě uživatelem definované nástroje. Ale nemůže používat tento proces, pokud vaše aplikace objekt není odvozen od [CWinAppEx Class](../mfc/reference/cwinappex-class.md). Další informace o přizpůsobení najdete v tématu [přizpůsobení pro prostředí MFC](../mfc/customization-for-mfc.md).  
  
 Pokud jste povolili podporu uživatelem definované nástroje, dialogové okno přizpůsobení automaticky zahrne **nástroje** kartě. Následující obrázek ukazuje **nástroje** stránky.  
  
 ![Nástroje pro kartě v dialogovém okně Upravit](../mfc/media/custdialogboxtoolstab.png "custdialogboxtoolstab")  
Přizpůsobení dialogové okno nástrojů, karta  
  
## <a name="enabling-user-defined-tools-support"></a>Povolení uživatelem definované nástroje podpory  
 Chcete-li povolit uživatelem definované nástroje v aplikaci, volejte [CWinAppEx::EnableUserTools](../mfc/reference/cwinappex-class.md#enableusertools). Ale nejdřív je nutné definovat několik konstanty v souborech prostředek vaší aplikace, které chcete použít jako parametry pro toto volání.  
  
 V editoru prostředků vytvořte fiktivní příkaz, který používá příslušný příkaz ID. V následujícím příkladu použijeme **ID_TOOLS_ENTRY** jako ID příkazu. Toto ID příkazu, který označuje umístění v nabídkách jeden nebo více rozhraní framework kde vloží uživatelem definované nástroje.  
  
 Si musí vyhradíte některé po sobě jdoucích ID v tabulce řetězec představující uživatelem definované nástroje. Počet řetězce, které si vyhradíte se rovná maximální počet uživatelů nástroje, které můžete definovat uživatele. V následujícím příkladu jsou pojmenované **ID_USER_TOOL1** prostřednictvím **ID_USER_TOOL10**.  
  
 Návrhy nabízejí uživatelům, aby věděli, vyberte adresářů a argumenty pro externí programy, které bude volána jako nástroje. K tomuto účelu vytvořte dva místní nabídky v editoru prostředků. V následujícím příkladu jsou pojmenované **IDR_MENU_ARGS** a **IDR_MENU_DIRS**. Každý příkaz v těchto nabídek definujte řetězec v tabulce řetězec vaší aplikace. ID prostředku řetězce musí být roven ID příkazu.  
  
 Můžete také vytvořit třídu odvozenou z [CUserTool třída](../mfc/reference/cusertool-class.md) nahradit výchozí implementace. K tomuto účelu předat informace o běhu programu pro odvozené třídy jako čtvrtého parametru CWinAppEx::EnableUserTools místo RUNTIME_CLASS ([CUserTool třída](../mfc/reference/cusertool-class.md)).  
  
 Po definování příslušné konstanty volání [CWinAppEx::EnableUserTools](../mfc/reference/cwinappex-class.md#enableusertools) povolit uživatelem definované nástroje.  
  
 Následující volání metody, které ukazuje, jak používat tyto konstanty:  
  
 [!code-cpp[NVC_MFC_VisualStudioDemo#1](../mfc/codesnippet/cpp/user-defined-tools_1.cpp)]  
  
 V tomto příkladu budou součástí kartě nástrojů **přizpůsobení** dialogové okno. Rozhraní framework nahradí libovolný příkaz, který odpovídá ID příkazu, který **ID_TOOLS_ENTRY** v jakékoli nabídku sadu nástrojů aktuálně definovaných uživatele vždy, když uživatel otevře této nabídky. Identifikátory příkazů **ID_USER_TOOL1** prostřednictvím **ID_USER_TOOL10** jsou rezervovány pro použití pro uživatelem definované nástroje. Třída [CUserTool třída](../mfc/reference/cusertool-class.md) zpracovává volání nástroje uživatele. Na kartě nástroj **přizpůsobení** dialogové okno obsahuje tlačítka napravo od pole zadání argumentů a adresář pro přístup k v nabídkách **IDR_MENU_ARGS** a **IDR_MENU_DIRS**. Když uživatel vybere příkaz z jednoho z těchto nabídek, systém připojí k příslušné textového pole řetězec, který má prostředek ID rovná ID příkazu.  
  
### <a name="including-predefined-tools"></a>Včetně předdefinovaného nástrojů  
 Pokud chcete předdefinovat některé nástroje při spuštění aplikace, je nutné přepsat [CFrameWnd::LoadFrame](../mfc/reference/cframewnd-class.md#loadframe) metoda hlavního okna vaší aplikace. V této metodě musíte provést následující kroky.  
  
##### <a name="to-add-new-tools-in-loadframe"></a>Přidání nových nástrojů v loadframe –  
  
1.  Získání ukazatele na [CUserToolsManager třída](../mfc/reference/cusertoolsmanager-class.md) objekt voláním [CWinAppEx::GetUserToolsManager](../mfc/reference/cwinappex-class.md#getusertoolsmanager).  
  
2.  Pro každý nástroj, který chcete vytvořit, volání [CUserToolsManager::CreateNewTool](../mfc/reference/cusertoolsmanager-class.md#createnewtool). Tato metoda vrátí ukazatel na [CUserTool třída](../mfc/reference/cusertool-class.md) objektu a přidá do interní kolekce nástrojů nástroje nově vytvořeného uživatele. Pokud jste zadali informace o běhu programu pro třídu odvozenou z [CUserTool třída](../mfc/reference/cusertool-class.md) jako čtvrtého parametru [CWinAppEx::EnableUserTools](../mfc/reference/cwinappex-class.md#enableusertools), [CUserToolsManager::CreateNewTool](../mfc/reference/cusertoolsmanager-class.md#createnewtool) se vytvořit instanci a místo nich vrácena instance této třídy.  
  
3.  Pro každý nástroj, nastavte jeho textový popisek nastavením `CUserTool::m_strLabel` a nastavit jeho příkaz voláním `CUserTool::SetCommand`. Výchozí implementaci [CUserTool třída](../mfc/reference/cusertool-class.md) automaticky načte dostupných ikon z program, který je zadaný ve volání `SetCommand`.  
  
## <a name="see-also"></a>Viz také  
 [Přizpůsobení pro prostředí MFC](../mfc/customization-for-mfc.md)   
 [CUserTool – třída](../mfc/reference/cusertool-class.md)   
 [CUserToolsManager – třída](../mfc/reference/cusertoolsmanager-class.md)   
 [CWinAppEx – třída](../mfc/reference/cwinappex-class.md)




