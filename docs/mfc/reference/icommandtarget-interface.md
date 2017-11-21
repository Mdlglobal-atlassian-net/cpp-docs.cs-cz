---
title: "Rozhraní ICommandTarget rozhraní | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ICommandTarget
- AFXWINFORMS/ICommandTarget
- AFXWINFORMS/ICommandTarget::Initialize
dev_langs: C++
helpviewer_keywords: ICommandTarget interface [MFC]
ms.assetid: dd9927f6-3479-4e7c-8ef9-13206cf901f3
caps.latest.revision: "27"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: a3a36bd4f3774c2dc6eb6cdf411d52049fbc4c61
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="icommandtarget-interface"></a>Rozhraní ICommandTarget rozhraní
Poskytuje uživatelského ovládacího prvku rozhraní přijímají příkazy ke zdrojovému objektu příkazu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
interface class ICommandTarget  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[ICommandTarget::Initialize](#initialize)|Inicializuje objekt cíl příkazu.|  
  
## <a name="remarks"></a>Poznámky  
 Pokud je hostitelem uživatelský ovládací prvek v zobrazení knihovny MFC [CWinFormsView](../../mfc/reference/cwinformsview-class.md) příkazy trasy a aktualizace příkaz zprávy uživatelského rozhraní do uživatelského ovládacího prvku tak, aby ji zpracovávat příkazy knihovny MFC (například rámec nabídky položek a tlačítka panelu nástrojů). Implementací `ICommandTarget`, poskytněte odkaz na uživatelský ovládací prvek [ICommandSource](../../mfc/reference/icommandsource-interface.md) objektu.  
  
 V tématu [postupy: přidání směrování příkazů do ovládacího prvku Windows Forms](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md) příklad použití `ICommandTarget`.  
  
 Další informace o používání Windows Forms najdete v tématu [pomocí uživatelského ovládacího prvku Windows Form v prostředí MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxwinforms.h (definovanou v atlmfc\lib\mfcmifc80.dll sestavení)  
  
##  <a name="initialize"></a>ICommandTarget::Initialize  
 Inicializuje objekt cíl příkazu.  
  
```  
void Initialize(ICommandSource^ cmdSource);  
```  
  
### <a name="parameters"></a>Parametry  
 `cmdSource`  
 Popisovač pro příkaz zdrojový objekt.  
  
### <a name="remarks"></a>Poznámky  
 Pokud je hostitelem uživatelský ovládací prvek v zobrazení knihovny MFC, CWinFormsView směřuje příkazy a aktualizace příkazů zpráv uživatelského rozhraní do uživatelského ovládacího prvku tak, aby ji zpracovávat příkazy knihovny MFC.  
  
 Tato metoda inicializuje cílový objekt příkazu a přidruží ji cmdSource zadaný příkaz zdrojový objekt. By měla být volána v implementaci třídy ovládacího prvku uživatele. Při inicializaci byste měli zaregistrovat ke zdrojovému objektu příkaz pomocí volání ICommandSource::AddCommandHandler implementace inicializace obslužné rutiny příkazů. V tématu Postupy: přidání směrování příkazů do ovládacího prvku Windows Forms příklad toho, jak to udělat pomocí inicializovat.  
  
## <a name="see-also"></a>Viz také  
 [Postupy: Přidání příkaz prvku směrování do ovládacího prvku Windows Forms](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md)   
 [ICommandSource rozhraní](../../mfc/reference/icommandsource-interface.md)



