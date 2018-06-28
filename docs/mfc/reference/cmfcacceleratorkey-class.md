---
title: Třída CMFCAcceleratorKey | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCAcceleratorKey
- AFXACCELERATORKEY/CMFCAcceleratorKey
- AFXACCELERATORKEY/CMFCAcceleratorKey::CMFCAcceleratorKey
- AFXACCELERATORKEY/CMFCAcceleratorKey::Format
- AFXACCELERATORKEY/CMFCAcceleratorKey::SetAccelerator
dev_langs:
- C++
helpviewer_keywords:
- CMFCAcceleratorKey [MFC], CMFCAcceleratorKey
- CMFCAcceleratorKey [MFC], Format
- CMFCAcceleratorKey [MFC], SetAccelerator
ms.assetid: d140fbf7-23db-45ea-a63e-414a5ec7b3d5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7e04bcdf797f7036d943219f9d067dcbf786cfa3
ms.sourcegitcommit: f1b051abb1de3fe96350be0563aaf4e960da13c3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/27/2018
ms.locfileid: "37039778"
---
# <a name="cmfcacceleratorkey-class"></a>CMFCAcceleratorKey – třída
Pomocná třída, která implementuje virtuální klíče mapování a formátování.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CMFCAcceleratorKey : public CObject  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CMFCAcceleratorKey::CMFCAcceleratorKey](#cmfcacceleratorkey)|Vytvoří `CMFCAcceleratorKey` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CMFCAcceleratorKey::Format](#format)|Přeloží k jeho vizuální znázornění strukturu AKCELERACE.|  
|[CMFCAcceleratorKey::SetAccelerator](#setaccelerator)|Nastaví klávesovou zkratku `CMFCAcceleratorKey` objektu.|  
  
## <a name="remarks"></a>Poznámky  
 Klávesy akcelerátoru se také označují jako klávesové zkratky. Pokud chcete zobrazit klávesové zkratky, které uživatel zadá, [CMFCAcceleratorKeyAssignCtrl třída](../../mfc/reference/cmfcacceleratorkeyassignctrl-class.md) mapy klávesové zkratky, jako je například Alt + Shift + S do formátu vlastní text, například "Alt + Shift + S". Každý `CMFCAcceleratorKey` objekt mapuje jeden klávesovou zkratku textovém formátu.  
  
 Další informace o tom, jak používat klávesové zkratky a tabulky akcelerátoru najdete v tématu [CKeyboardManager třída](../../mfc/reference/ckeyboardmanager-class.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak vytvořit `CMFCAcceleratorKey` objekt a jak používat jeho `Format` metoda.  
  
 [!code-cpp[NVC_MFC_RibbonApp#30](../../mfc/reference/codesnippet/cpp/cmfcacceleratorkey-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CMFCAcceleratorKey`   
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxacceleratorkey.h  
  
##  <a name="cmfcacceleratorkey"></a>  CMFCAcceleratorKey::CMFCAcceleratorKey  
 Vytvoří [CMFCAcceleratorKey](../../mfc/reference/cmfcacceleratorkey-class.md) objektu.  
  
```  
CMFCAcceleratorKey();  
CMFCAcceleratorKey(LPACCEL lpAccel);
```  
  
### <a name="parameters"></a>Parametry  
 [v] *lpAccel*  
 Ukazatel na klávesovou zkratku.  
  
### <a name="remarks"></a>Poznámky  
 Pokud nezadáte klávesovou zkratku při vytváření `CMFCAccleratorKey`, použijte [CMFCAcceleratorKey::SetAccelerator](#setaccelerator) metoda, jak přidružit klávesovou zkratku s vaší `CMFCAcceleratorKey` objektu.  
  
##  <a name="format"></a>  CMFCAcceleratorKey::Format  
 Přeloží strukturu AKCELERACE k jeho přidružené řetězcovou hodnotu.  
  
```  
void Format(CString& str) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [out] *str*  
 Odkaz na `CString` objektu, kde metodu zapíše přeložený klávesovou zkratku.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda načte řetězec formátu přidružené klávesovou zkratku. Můžete nastavit řetězec formátu [CMFCAcceleratorKey](../../mfc/reference/cmfcacceleratorkey-class.md) pomocí konstruktoru nebo metodu [CMFCAcceleratorKey::SetAccelerator](#setaccelerator).  
  
##  <a name="setaccelerator"></a>  CMFCAcceleratorKey::SetAccelerator  
 Nastaví klávesovou zkratku [CMFCAcceleratorKey](../../mfc/reference/cmfcacceleratorkey-class.md) objektu.  
  
```  
void SetAccelerator(LPACCEL lpAccel);
```  
  
### <a name="parameters"></a>Parametry  
 [v] *lpAccel*  
 Ukazatel na klávesovou zkratku.  
  
### <a name="remarks"></a>Poznámky  
 Pomocí této metody můžete nastavit klávesovou zkratku `CMFCAcceleratorKey` Pokud není zadán klávesovou zkratku při vytváření `CMFCAcceleratorKey`.  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Třídy](../../mfc/reference/mfc-classes.md)   
 [CKeyboardManager – třída](../../mfc/reference/ckeyboardmanager-class.md)
