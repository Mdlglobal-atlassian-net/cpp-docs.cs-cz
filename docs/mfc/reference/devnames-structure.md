---
title: "DEVNAMES – struktura | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- DEVNAMES
dev_langs:
- C++
helpviewer_keywords:
- DEVNAMES [MFC]
ms.assetid: aac97f60-2169-471a-ba5d-c0baed9eed9a
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a3627af10dfb6fd18c54f772d26c33123127613a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="devnames-structure"></a>DEVNAMES – struktura
`DEVNAMES` Struktura obsahuje řetězců, které identifikují ovladače, zařízení a názvy výstupní port pro tiskárny.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef struct tagDEVNAMES { /* dvnm */  
    WORD wDriverOffset;  
    WORD wDeviceOffset;  
    WORD wOutputOffset;  
    WORD wDefault; */* driver,
    device,
    and port-name strings follow wDefault */  
} DEVNAMES;  
```  
  
#### <a name="parameters"></a>Parametry  
 *wDriverOffset*  
 (Vstup/výstup) Určuje posun ve znacích na řetězec ukončené hodnotou null, který obsahuje název souboru (bez přípony) ovladače zařízení. Na vstupu tento řetězec se používá k určení tiskárny pro zobrazení původně v dialogovém okně.  
  
 *wDeviceOffset*  
 (Vstup/výstup) Určuje posunutí v znaků řetězce ukončené hodnotou null (maximálně 32 bajtů včetně hodnotu null), který obsahuje název zařízení. Tento řetězec musí být stejný jako **dmDeviceName** členem [DEVMODE](http://msdn.microsoft.com/library/windows/desktop/dd183565) struktura.  
  
 *wOutputOffset*  
 (Vstup/výstup) Určuje posunutí v znaků do řetězce ukončené hodnotou null, který obsahuje název zařízení DOS pro fyzické výstup střední (výstupní port).  
  
 *wDefault*  
 Určuje, zda řetězce součástí `DEVNAMES` struktura identifikovat tiskárny výchozí. Tento řetězec se používá k ověření, že se tiskárny výchozí nezměnil od poslední operaci tisku. Vstupní, je-li **DN_DEFAULTPRN** nastavený příznak, ostatní hodnoty `DEVNAMES` struktura jsou zkontrolován výchozí tiskárnu. Pokud některý řetězec neshodují, se zobrazí zpráva s upozorněním informující uživatele, který dokument muset naformátována. Na výstupu **wDefault** člen se změní jenom v případě, že se zobrazí dialogové okno Nastavení tisku a Uživatel reagoval na tlačítko OK. **DN_DEFAULTPRN** je příznak nastaven, pokud jste vybrali výchozí tiskárny. Pokud je vybrána konkrétní tiskárnu, není nastaven příznak. Všechny bity v tento člen je vyhrazeno pro interní použití pole procedurou dialogové okno tisku.  
  
## <a name="remarks"></a>Poznámky  
 **PrintDlg** funkce používá tyto řetězce k chybě při inicializaci členů v dialogových oken tiskových definovaná systémem. Když uživatel zavře dialogové okno, v této struktuře se vrátí informace o vybrané tiskárny.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** commdlg.h  
  
## <a name="see-also"></a>Viz také  
 [Struktury, styly, zpětná volání a mapy zpráv](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CPrintDialog::CreatePrinterDC](../../mfc/reference/cprintdialog-class.md#createprinterdc)


