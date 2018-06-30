---
title: DEVNAMES – struktura | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- DEVNAMES
dev_langs:
- C++
helpviewer_keywords:
- DEVNAMES [MFC]
ms.assetid: aac97f60-2169-471a-ba5d-c0baed9eed9a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0c13167c42c6acbfcc5f3af500205eed6ab884d9
ms.sourcegitcommit: 208d445fd7ea202de1d372d3f468e784e77bd666
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/29/2018
ms.locfileid: "37121572"
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
 (Vstup/výstup) Určuje posunutí v znaků řetězce ukončené hodnotou null (maximálně 32 bajtů včetně hodnotu null), který obsahuje název zařízení. Tento řetězec musí být stejný jako `dmDeviceName` členem [DEVMODE](http://msdn.microsoft.com/library/windows/desktop/dd183565) struktura.  
  
 *wOutputOffset*  
 (Vstup/výstup) Určuje posunutí v znaků do řetězce ukončené hodnotou null, který obsahuje název zařízení DOS pro fyzické výstup střední (výstupní port).  
  
 *wDefault*  
 Určuje, zda řetězce součástí `DEVNAMES` struktura identifikovat tiskárny výchozí. Tento řetězec se používá k ověření, že se tiskárny výchozí nezměnil od poslední operaci tisku. Na vstupu, pokud je nastavený příznak DN_DEFAULTPRN, dalších hodnot v `DEVNAMES` struktura jsou zkontrolován výchozí tiskárnu. Pokud některý řetězec neshodují, se zobrazí zpráva s upozorněním informující uživatele, který dokument muset naformátována. Na výstupu `wDefault` člen se změní jenom v případě, že se zobrazí dialogové okno Nastavení tisku a Uživatel reagoval na tlačítko OK. Příznak DN_DEFAULTPRN je nastavit, pokud jste vybrali výchozí. Pokud je vybrána konkrétní tiskárnu, není nastaven příznak. Všechny bity v tento člen je vyhrazeno pro interní použití pole procedurou dialogové okno tisku.  
  
## <a name="remarks"></a>Poznámky  
 `PrintDlg` Funkce používá tyto řetězce k chybě při inicializaci členů v dialogových oken tiskových definovaná systémem. Když uživatel zavře dialogové okno, v této struktuře se vrátí informace o vybrané tiskárny.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** commdlg.h  
  
## <a name="see-also"></a>Viz také  
 [Struktury, styly, zpětná volání a mapy zpráv](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CPrintDialog::CreatePrinterDC](../../mfc/reference/cprintdialog-class.md#createprinterdc)


