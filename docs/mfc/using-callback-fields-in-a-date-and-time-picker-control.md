---
title: "Použití polí zpětného volání v výběr data a času řízení | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- DTN_FORMATQUERY
- DTN_FORMAT
dev_langs: C++
helpviewer_keywords:
- DateTimePicker control [MFC], callback fields
- callback fields in CDateTimeCtrl class [MFC]
- CDateTimeCtrl class [MFC], callback fields
- CDateTimeCtrl class [MFC], handling DTN_FORMAT and DTN_FORMATQ
- DTN_FORMATQUERY notification [MFC]
- DTN_FORMAT notification [MFC]
- DateTimePicker control [MFC]
ms.assetid: 404f4ba9-cba7-4718-9faa-bc6b274a723f
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 9e5526b0f8826a91eb0b1c5a6eae250abbb02fcf
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="using-callback-fields-in-a-date-and-time-picker-control"></a>Použití polí zpětného volání v ovládacím prvku pro výběr data a času
Kromě standardní formát znaky, které definují polích pro výběr data a času můžete přizpůsobit výstupu tak, že zadáte určité části vlastní řetězec formátu jako pole zpětného volání. Chcete-li deklarovat pole zpětného volání, obsahovat jeden nebo více znaků "X" (ASCII kód 88) kdekoli v těle řetězec formátu. Například následující řetězec "" Dnes je: "rr" /, MM, nebo 'dd' (den 'X')'"způsobí, že zobrazit aktuální hodnotu jako rok a měsíc, datum a nakonec den v roce prvku pro výběr datum a čas.  
  
> [!NOTE]
>  Počet značkou v zpětné volání neodpovídá pole počet znaků, které se zobrazí.  
  
 Možné rozlišit mezi více polí zpětného volání ve vlastním řetězcem opakováním znak "X". Proto řetězec formátu "XXddddMMMdd', ' yyyXXX" obsahuje dvě pole jedinečný zpětného volání, "XX" a "XXX".  
  
> [!NOTE]
>  Pole zpětného volání jsou považovány za platné pole, aplikace musí být připraveno pro zpracování **DTN_WMKEYDOWN** zpráv s oznámením.  
  
 Implementace pole zpětného volání v ovládacím prvku vaše datum a čas pro výběr se skládá ze tří částí:  
  
-   Inicializace vlastní řetězec formátu  
  
-   Zpracování **dtn_formatquery –** oznámení  
  
-   Zpracování **dtn_format –** oznámení  
  
## <a name="initializing-the-custom-format-string"></a>Inicializace vlastní řetězec formátu  
 Inicializuje pomocí volání vlastní řetězec `CDateTimeCtrl::SetFormat`. Další informace najdete v tématu [pomocí vlastní formátu řetězce na datum a čas ovládací prvek výběru](../mfc/using-custom-format-strings-in-a-date-and-time-picker-control.md). Běžné místo, kde můžete nastavit vlastní řetězec formátu probíhá `OnInitDialog` funkce vlastní obsahující třídy dialogového okna nebo `OnInitialUpdate` funkce třídy obsahující zobrazení.  
  
## <a name="handling-the-dtnformatquery-notification"></a>Zpracování dtn_formatquery – oznámení  
 Pokud ovládací prvek analyzuje řetězec formátu a zaznamená pole zpětného volání, odešle aplikace **dtn_format –** a **dtn_formatquery –** zpráv s oznámením. Řetězec pole zpětného volání je součástí oznámení, takže můžete určit, které pole zpětného volání je která je dotazována.  
  
 **Dtn_formatquery –** oznámení se odesílá načíst maximální povolenou velikost v pixelech řetězec, který se zobrazí v poli aktuální zpětného volání.  
  
 Chcete-li tuto hodnotu vypočítat správně, je nutné vypočítat výška a šířka řetězec, který má být nahrazena v poli pomocí ovládacího prvku zobrazení písma. Skutečné výpočet řetězce, který lze snadno dosáhnout pomocí volání [GetTextExtentPoint32](http://msdn.microsoft.com/library/windows/desktop/dd144938) Win32 funkce. Jakmile velikost je určena, předat hodnotu zpět do aplikace a ukončete obslužné rutiny.  
  
 V následujícím příkladu je jedna z metod poskytnutí velikost řetězce zpětného volání:  
  
 [!code-cpp[NVC_MFCControlLadenDialog#8](../mfc/codesnippet/cpp/using-callback-fields-in-a-date-and-time-picker-control_1.cpp)]  
  
 Jakmile je vypočítána velikost pole aktuálního zpětného volání, musíte zadat hodnotu pro pole. To se provádí v obslužnou rutinu pro **dtn_format –** oznámení.  
  
## <a name="handling-the-dtnformat-notification"></a>Zpracování dtn_format – oznámení  
 **Dtn_format –** oznámení aplikací slouží k vyžádání řetězcem znaků, která má být nahrazena. Následující příklad ukazuje jeden možný způsob:  
  
 [!code-cpp[NVC_MFCControlLadenDialog#9](../mfc/codesnippet/cpp/using-callback-fields-in-a-date-and-time-picker-control_2.cpp)]  
  
> [!NOTE]
>  Ukazatele myši **NMDATETIMEFORMAT** struktura zjistí, že přetypování první parametr správný typ. obslužná rutina oznámení.  
  
## <a name="see-also"></a>Viz také  
 [Používání atributu CDateTimeCtrl](../mfc/using-cdatetimectrl.md)   
 [Ovládací prvky](../mfc/controls-mfc.md)

