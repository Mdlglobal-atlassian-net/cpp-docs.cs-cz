---
title: "Přizpůsobení klávesnice a myši | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- customizations [MFC], keyboard and mouse (MFC Extensions)
- keyboard and mouse customizations (MFC Extensions)
ms.assetid: 1f789f1b-5f2e-4b11-b974-e3e2a2e49d82
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1b031c4af05df7ad2b8c0850cefb116d4ac249d7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="keyboard-and-mouse-customization"></a>Přizpůsobení klávesnice a myši
MFC umožňuje uživateli vaší aplikace k přizpůsobení jak zpracovává klávesnici a myš vstup. Uživatel může přizpůsobit vstup z klávesnice přiřazením klávesové zkratky příkazy. Uživatele můžete také upravit vstup myši vyberte příkaz, který se má provést při poklepání uvnitř windows konkrétní aplikace. Toto téma vysvětluje, jak přizpůsobit vstup pro vaši aplikaci.  
  
 V **přizpůsobení** dialogové okno, uživatel může změnit vlastní ovládací prvky pro myši a klávesnice. K zobrazení tohoto dialogového okna, uživatel bodů **přizpůsobit** na **zobrazení** nabídce a poté klikne na tlačítko **panely nástrojů a stabilní umístění**. V dialogovém okně uživatel klikne, buď **klávesnice** kartě nebo **myši** kartě.  
  
## <a name="keyboard-customization"></a>Přizpůsobení klávesnice  
 Následující obrázek ukazuje **klávesnice** kartě **přizpůsobení** dialogové okno.  
  
 ![V dialogovém okně Upravit na kartě klávesnice](../mfc/media/mfcnextkeyboardtab.png "mfcnextkeyboardtab")  
Na kartě přizpůsobení klávesnice  
  
 Uživatel pracuje se na kartě klávesnice, přiřadit jeden nebo více klávesové zkratky pro příkaz. Na levé straně na kartě jsou uvedeny dostupné příkazy. Uživatele můžete vybrat libovolný příkaz k dispozici v nabídce. Příkazy nabídky může být přidružen klávesové zkratky. Poté, co uživatel zadá nový zástupce odkazující **přiřadit** aktivuje tlačítko. Po kliknutí na toto tlačítko, aplikace vybraný příkaz přidruží tento zástupce.  
  
 V pravém sloupci v seznamu jsou uvedeny všechny aktuálně přidělené klávesové zkratky. Uživatele můžete také vybrat jednotlivé klávesové zkratky a je odebrat nebo resetovat všechna mapování pro aplikaci.  
  
 Pokud chcete podporovat toto vlastní nastavení v aplikaci, musíte vytvořit [CKeyboardManager](../mfc/reference/ckeyboardmanager-class.md) objektu. Chcete-li vytvořit `CKeyboardManager` objektu, zavolejte funkci [CWinAppEx::InitKeyboardManager](../mfc/reference/cwinappex-class.md#initkeyboardmanager). Tato metoda vytvoří a inicializuje manažera klávesnice. Pokud vytvoříte klávesnici správce ručně, stále musí volat `CWinAppEx::InitKeyboardManager` k chybě při inicializaci ho.  
  
 Pokud použijete průvodce k vytvoření aplikace, průvodce se inicializace správce klávesnice. Po aplikaci inicializuje správce klávesnice, přidá rozhraní **klávesnice** kartu k **přizpůsobení** dialogové okno.  
  
## <a name="mouse-customization"></a>Přizpůsobení myši  
 Následující obrázek ukazuje **myši** kartě **přizpůsobení** dialogové okno.  
  
 ![Karta myši v dialogovém okně Upravit](../mfc/media/mfcnextmousetab.png "mfcnextmousetab")  
Karta přizpůsobení myši  
  
 Uživatel pracuje se na této kartě přiřadit nabídky příkazu myš, dvakrát klikněte na akci. Uživatel vybere zobrazení z levé straně okna a potom pomocí ovládacích prvků na pravé straně příkaz přidružit akce poklikejte na soubor. Poté, co uživatel klikne na tlačítko **Zavřít**, aplikace provede příkaz přidružené vždy, když uživatel poklikáním kdekoli v zobrazení.  
  
 Ve výchozím nastavení přizpůsobení myši není povoleno, když vytvoříte aplikaci pomocí průvodce.  
  
#### <a name="to-enable-mouse-customization"></a>Za účelem přizpůsobení myši  
  
1.  Inicializace [CMouseManager](../mfc/reference/cmousemanager-class.md) objekt voláním [CWinAppEx::InitMouseManager](../mfc/reference/cwinappex-class.md#initmousemanager).  
  
2.  Získání ukazatele na správce myši s použitím [CWinAppEx::GetMouseManager](../mfc/reference/cwinappex-class.md#getmousemanager).  
  
3.  Přidání zobrazení do správce myši s použitím [CMouseManager::AddView](../mfc/reference/cmousemanager-class.md#addview) metoda. To lze proveďte pro každé zobrazení, které chcete přidat do správce myši.  
  
 Po aplikaci inicializuje správce myš, přidá rozhraní **myši** kartu k **přizpůsobit** dialogové okno. Pokud je nemůžete přidat žádné zobrazení, na kartě způsobí, že k neošetřené výjimce. Po vytvoření seznamu zobrazení, **myši** karta je k dispozici pro uživatele.  
  
 Když přidáte nové zobrazení pro správce myš, můžete jí jedinečný identifikátor. Pokud chcete pro podporu myši přizpůsobení okna, je nutné zpracovat `WM_LBUTTONDBLCLICK` zprávu a volání [CWinAppEx::OnViewDoubleClick](../mfc/reference/cwinappex-class.md#onviewdoubleclick) funkce. Při volání této funkce je jeden z parametrů ID pro toto okno. Je zodpovědností programátorů ke sledování čísla ID a objekty s nimi spojených.  
  
## <a name="security-concerns"></a>Aspekty zabezpečení  
 Jak je popsáno v [uživatelem definované nástroje](../mfc/user-defined-tools.md), uživatele můžete přidružit uživatelem definované nástroje ID události poklikejte na soubor. Při poklepání zobrazení aplikace vyhledá uživatele nástroj, který odpovídá přidružené ID. Pokud aplikace najde odpovídající nástroj, provede nástroj. Pokud aplikace nemůže najít odpovídající nástroj, odešle wm_command – zprávy s ID zobrazení, který byl dvakrát kliknete.  
  
 Přizpůsobené nastavení jsou uloženy v registru. Úpravou registru můžete nahradit útočník platné nástroj ID uživatele libovolný příkaz. Při poklepání zobrazení, zobrazení zpracuje příkaz, který útočník vysazeny. To může způsobit neočekávané a potenciálně nebezpečné chování.  
  
 Kromě toho tento typ útoku obejít ochrana uživatelské rozhraní. Předpokládejme například, že aplikace má tisk zakázána. To znamená v jeho uživatelském rozhraní **tiskových** tlačítko a nabídky jsou k dispozici. Obvykle to brání aplikaci v tisku. Ale pokud útočník upravit registr, uživatel může nyní může odeslat příkaz pro tisk přímo poklepáním na zobrazení, obcházení prvky uživatelského rozhraní, které jsou k dispozici.  
  
 Ochrana proti tento typ útoku, přidávání kódu do vaší aplikace obslužná rutina k ověření, že příkaz platná před jeho spuštěním. Nezávisí na uživatelské rozhraní zabránit příkaz odesílány do aplikace.  
  
## <a name="see-also"></a>Viz také  
 [Přizpůsobení pro prostředí MFC](../mfc/customization-for-mfc.md)   
 [CKeyboardManager – třída](../mfc/reference/ckeyboardmanager-class.md)   
 [CMouseManager – třída](../mfc/reference/cmousemanager-class.md)   
 [Vliv přizpůsobení na zabezpečení](../mfc/security-implications-of-customization.md)

