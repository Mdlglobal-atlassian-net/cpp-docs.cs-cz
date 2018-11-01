---
title: Uživatelem definované nástroje
ms.date: 11/04/2016
helpviewer_keywords:
- user-defined tools (MFC Extensions)
ms.assetid: cb887421-78ce-4652-bc67-96a53984ccaa
ms.openlocfilehash: 5c5773cdbbd641b30f39494b2d11c282d2d43954
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50607074"
---
# <a name="user-defined-tools"></a>Uživatelem definované nástroje

MFC podporuje uživatelem definované nástroje. Uživatelsky definovaného nástroje je zvláštní příkaz, který se spustí externí, zadané uživatelem programu. Proces přizpůsobení můžete použít ke správě uživatelem definované nástroje. Ale nemůže použít tento proces, pokud aplikační objekt není odvozen od [CWinAppEx – třída](../mfc/reference/cwinappex-class.md). Další informace o přizpůsobení najdete v tématu [přizpůsobení pro prostředí MFC](../mfc/customization-for-mfc.md).

Pokud je povolena podpora uživatelem definované nástroje, dialogové okno přizpůsobení automaticky zahrne **nástroje** kartu. Je vidět na následujícím obrázku **nástroje** stránky.

![V dialogovém okně vlastní kartě nástroje](../mfc/media/custdialogboxtoolstab.png "custdialogboxtoolstab") přizpůsobení dialogové okno nástrojů, karta

## <a name="enabling-user-defined-tools-support"></a>Povolení uživatelem definované nástroje podpory

Chcete-li povolit uživatelem definované nástroje v aplikaci, zavolejte [CWinAppEx::EnableUserTools](../mfc/reference/cwinappex-class.md#enableusertools). Ale je nutné nejprve definovat několik konstant v souborech prostředků vaší aplikace, které chcete použít jako parametry pro toto volání.

V editoru prostředků vytvořte fiktivního příkaz, který používá příslušný příkaz identifikátor. V následujícím příkladu vytvoříme s využitím `ID_TOOLS_ENTRY` jako ID příkazu. Toto ID příkaz označuje umístění v jedné nebo více nabídek, kde bude rozhraní framework vložit uživatelem definované nástroje.

Je nutné nastavit jste si poznamenali několik po sobě jdoucích ID v tabulce řetězec představující uživatelem definované nástroje. Počet řetězců, které jste nastavili jste si poznamenali je rovna hodnotě maximální počet uživatelských nástrojů, které uživatelé mohli definovat. V následujícím příkladu jsou pojmenovány `ID_USER_TOOL1` prostřednictvím `ID_USER_TOOL10`.

Návrhy můžete nabídnout uživatelům, aby to pomohl ostatním vyberte adresářů a argumenty pro externí programy, které bude volána jako nástroje. K tomu, vytvořte dva místní nabídky v editoru prostředků. V následujícím příkladu jsou pojmenovány `IDR_MENU_ARGS` a `IDR_MENU_DIRS`. Pro každý příkaz v těchto nabídek definujte řetězec v tabulce řetězců vaší aplikace. ID prostředku řetězce musí být rovna ID příkazu.

Můžete také vytvořit třídu odvozenou z [cusertool – třída](../mfc/reference/cusertool-class.md) nahradit výchozí implementaci. K tomuto účelu předat informace o modulu runtime pro odvozené třídy jako čtvrtý parametr v CWinAppEx::EnableUserTools místo RUNTIME_CLASS ([cusertool – třída](../mfc/reference/cusertool-class.md)).

Po definování konstant odpovídající volání [CWinAppEx::EnableUserTools](../mfc/reference/cwinappex-class.md#enableusertools) povolit uživatelem definované nástroje.

Následující volání metody, které ukazuje, jak používat tyto konstanty:

[!code-cpp[NVC_MFC_VisualStudioDemo#1](../mfc/codesnippet/cpp/user-defined-tools_1.cpp)]

V tomto příkladu bude součástí na kartě nástrojů **přizpůsobení** dialogové okno. Rozhraní framework nahradí jakýkoli příkaz, který se shoduje s Identifikátorem příkazu `ID_TOOLS_ENTRY` v jakékoliv nabídky se sadou nástrojů aktuálně definovaných uživatele pokaždé, když uživatel otevře této nabídky. Identifikátory příkazů `ID_USER_TOOL1` prostřednictvím `ID_USER_TOOL10` jsou vyhrazené pro použití pro uživatelem definované nástroje. Třída [cusertool – třída](../mfc/reference/cusertool-class.md) zpracovává volání uživatelské nástroje. Na kartě nástroj **přizpůsobení** dialogové okno obsahuje tlačítka vpravo od pole zadání argumentu a adresář pro přístup k nabídky **IDR_MENU_ARGS** a **IDR_MENU_DIRS**. Když uživatel vybere příkaz z jednoho z těchto nabídek, přidá rozhraní do příslušného textového pole řetězec, který má stejné ID příkazu. ID prostředku

### <a name="including-predefined-tools"></a>Včetně předdefinovaných nástrojů

Pokud chcete pro předdefinování některé nástroje při spuštění aplikace, je nutné přepsat [CFrameWnd::LoadFrame](../mfc/reference/cframewnd-class.md#loadframe) metoda hlavního okna aplikace. V této metodě musíte provést následující kroky.

##### <a name="to-add-new-tools-in-loadframe"></a>Přidání nových nástrojů v loadframe –

1. Získat ukazatel [cusertoolsmanager – třída](../mfc/reference/cusertoolsmanager-class.md) objektu voláním [CWinAppEx::GetUserToolsManager](../mfc/reference/cwinappex-class.md#getusertoolsmanager).

1. Pro každý nástroj, který chcete vytvořit, volání [CUserToolsManager::CreateNewTool](../mfc/reference/cusertoolsmanager-class.md#createnewtool). Tato metoda vrací ukazatel [cusertool – třída](../mfc/reference/cusertool-class.md) objektu a přidá nově vytvořené uživatelské nástroje do interní kolekce nástroje. Pokud je k dispozici informace o modulu runtime pro odvozenou třídu [cusertool – třída](../mfc/reference/cusertool-class.md) jako čtvrtý parametr [CWinAppEx::EnableUserTools](../mfc/reference/cwinappex-class.md#enableusertools), [CUserToolsManager::CreateNewTool](../mfc/reference/cusertoolsmanager-class.md#createnewtool) bude vytvářet instanci a vracet instanci této třídy místo toho.

1. Pro každý nástroj nastavením jeho textový popisek `CUserTool::m_strLabel` a nastavit jeho příkaz voláním `CUserTool::SetCommand`. Výchozí implementace [cusertool – třída](../mfc/reference/cusertool-class.md) automaticky načte dostupné ikony z programu, který je zadaný ve volání `SetCommand`.

## <a name="see-also"></a>Viz také

[Přizpůsobení pro prostředí MFC](../mfc/customization-for-mfc.md)<br/>
[CUserTool – třída](../mfc/reference/cusertool-class.md)<br/>
[CUserToolsManager – třída](../mfc/reference/cusertoolsmanager-class.md)<br/>
[CWinAppEx – třída](../mfc/reference/cwinappex-class.md)

