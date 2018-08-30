---
title: Cmetafiledc – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMetaFileDC
- AFXEXT/CMetaFileDC
- AFXEXT/CMetaFileDC::CMetaFileDC
- AFXEXT/CMetaFileDC::Close
- AFXEXT/CMetaFileDC::CloseEnhanced
- AFXEXT/CMetaFileDC::Create
- AFXEXT/CMetaFileDC::CreateEnhanced
dev_langs:
- C++
helpviewer_keywords:
- CMetaFileDC [MFC], CMetaFileDC
- CMetaFileDC [MFC], Close
- CMetaFileDC [MFC], CloseEnhanced
- CMetaFileDC [MFC], Create
- CMetaFileDC [MFC], CreateEnhanced
ms.assetid: ffce60fa-4181-4d46-9832-25e46fad4db4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fb2fd794798f96cceca893df4a69dc888196d9a6
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43197000"
---
# <a name="cmetafiledc-class"></a>Cmetafiledc – třída
Implementuje metasoubor systému Windows, který obsahuje posloupnost grafiky zařízení (GDI) příkazy, které můžete zopakovat pro vytvoření požadovaného obrázku nebo textu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CMetaFileDC : public CDC  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CMetaFileDC::CMetaFileDC](#cmetafiledc)|Vytvoří `CMetaFileDC` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CMetaFileDC::Close](#close)|Ukončí kontext zařízení a vytvoří metasoubor popisovač.|  
|[CMetaFileDC::CloseEnhanced](#closeenhanced)|Objekt context enhanced metafile zařízení se zavře a vytvoří popisovač enhanced metafile.|  
|[CMetaFileDC::Create](#create)|Vytvoří kontextu zařízení metasouboru Windows a připojí ho k `CMetaFileDC` objektu.|  
|[CMetaFileDC::CreateEnhanced](#createenhanced)|Vytvoří metasoubor kontext zařízení pro metasoubor rozšířeného formátu.|  
  
## <a name="remarks"></a>Poznámky  
 K implementaci metasoubor systému Windows, nejprve vytvořte `CMetaFileDC` objektu. Vyvolat `CMetaFileDC` konstruktor, poté zavolejte [vytvořit](#create) členskou funkci, která vytvoří kontextu zařízení metasouboru Windows a připojí ho k `CMetaFileDC` objektu.  
  
 Potom pošle `CMetaFileDC` objekt sekvence CDC GDI příkazy, které jsou určené pro něj znovu přehrát. Pouze GDI příkazy, které vytvoří výstup, jako například `MoveTo` a `LineTo`, lze použít.  
  
 Po odeslání požadované příkazy metasoubor volání `Close` členské funkce, která uzavře metasouborů kontexty zařízení a vrátí popisovač metasouboru. Potom `CMetaFileDC` objektu.  
  
 [CDC::PlayMetaFile](../../mfc/reference/cdc-class.md#playmetafile) popisovač metasouboru. poté použít k přehrávání metasoubor opakovaně. Tento metasoubor lze také ovládat pomocí funkcí Windows, jako [CopyMetaFile](/windows/desktop/api/wingdi/nf-wingdi-copymetafilea), který zkopíruje metasoubor na disk.  
  
 Pokud je tento metasoubor už nepotřebujete, odstraňte ho z paměti s [DeleteMetaFile](/windows/desktop/api/wingdi/nf-wingdi-deletemetafile) funkce Windows.  
  
 Můžete také implementovat `CMetaFileDC` objektu tak, aby ji zvládne výstup volání i atribut GDI volání, jako `GetTextExtent`. Takové metasoubor je flexibilnější a můžete informace snadno opakovaně použít obecné rozhraní GDI kód, který se často se skládá z kombinace volání výstup a atribut. `CMetaFileDC` Třída dědí dvě kontexty zařízení `m_hDC` a `m_hAttribDC`, z CSP. `m_hDC` Kontextu zařízení zpracovává všechny [CDC](../../mfc/reference/cdc-class.md) GDI výstup volání a `m_hAttribDC` kontextu zařízení zpracovává všechna volání rozhraní GDI CDC atribut. Za normálních okolností kontexty tyto dvě zařízení odkazovat do stejného zařízení. V případě třídy `CMetaFileDC`, atribut řadič domény je standardně nastavená na hodnotu NULL.  
  
 Vytvoření druhého kontextu zařízení, na které odkazuje na obrazovce, tiskárna nebo zařízení, které metasoubor, pak volat `SetAttribDC` členskou funkci přidružit nový kontext zařízení s `m_hAttribDC`. Volání rozhraní GDI informace teď budou směrovány do nového `m_hAttribDC`. Výstup GDI volání budou moct `m_hDC`, která představuje metasoubor.  
  
 Další informace o `CMetaFileDC`, naleznete v tématu [kontexty zařízení](../../mfc/device-contexts.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [Třídy CObject](../../mfc/reference/cobject-class.md)  
  
 [CDC](../../mfc/reference/cdc-class.md)  
  
 `CMetaFileDC`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxext.h  
  
##  <a name="close"></a>  CMetaFileDC::Close  
 Zavře kontextu zařízení metasouboru a vytvoří Windows metafile popisovač, který slouží k přehrávání metasoubor pomocí [CDC::PlayMetaFile](../../mfc/reference/cdc-class.md#playmetafile) členskou funkci.  
  
```  
HMETAFILE Close();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Platný HMETAFILE, pokud je funkce úspěšná. v opačném případě hodnota NULL.  
  
### <a name="remarks"></a>Poznámky  
 Popisovač Windows metafile lze také použít k manipulaci s metasoubor s funkcemi Windows, jako [CopyMetaFile](/windows/desktop/api/wingdi/nf-wingdi-copymetafilea).  
  
 Odstranit tento metasoubor po použití voláním Windows [DeleteMetaFile](/windows/desktop/api/wingdi/nf-wingdi-deletemetafile) funkce.  
  
##  <a name="closeenhanced"></a>  CMetaFileDC::CloseEnhanced  
 Objekt context enhanced metafile zařízení se zavře a vrátí popisovač, který identifikuje metasoubor rozšířeného formátu.  
  
```  
HENHMETAFILE CloseEnhanced();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Popisovač rozšířený metasoubor, v případě úspěchu; v opačném případě hodnota NULL.  
  
### <a name="remarks"></a>Poznámky  
 Aplikace může použít rozšířený metasoubor popisovač vrácený touto funkcí provádět následující úlohy:  
  
-   Zobrazí informace uložené v rozšířený metasoubor  
  
-   Vytvoření kopie rozšířený metasoubor  
  
-   Zobrazení výčtu, upravit nebo zkopírujte jednotlivé záznamy v rozšířený metasoubor  
  
-   Načíst volitelný popis obsahu metasoubor z hlavičky rozšířený metasoubor  
  
-   Načíst kopii EMF – hlavička  
  
-   Načíst binární kopie rozšířený metasoubor  
  
-   Výčet barev v paletě volitelné  
  
-   Převést na formát Windows metafile rozšířeného formátu metasoubor  
  
 Pokud aplikace nepotřebuje EMF popisovač, by měla uvolnit popisovač voláním rozhraní Win32 `DeleteEnhMetaFile` funkce.  
  
##  <a name="cmetafiledc"></a>  CMetaFileDC::CMetaFileDC  
 Vytvoření `CMetaFileDC` objektu ve dvou krocích.  
  
```  
CMetaFileDC();
```  
  
### <a name="remarks"></a>Poznámky  
 Nejprve volat `CMetaFileDC`, zavolejte `Create`, vytvoří kontextu zařízení metasouboru Windows a připojí ho k `CMetaFileDC` objektu.  
  
##  <a name="create"></a>  CMetaFileDC::Create  
 Vytvoření `CMetaFileDC` objektu ve dvou krocích.  
  
```  
BOOL Create(LPCTSTR lpszFilename = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 *lpszFilename*  
 Odkazuje na řetězec znaků zakončené znakem null. Určuje název souboru metasoubor k vytvoření. Pokud *lpszFilename* má hodnotu NULL, je vytvořen nový metasoubor v paměti.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové, pokud je funkce úspěšná; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Nejprve volat konstruktor `CMetaFileDC`, zavolejte `Create`, vytvoří kontextu zařízení metasouboru Windows a připojí ho k `CMetaFileDC` objektu.  
  
##  <a name="createenhanced"></a>  CMetaFileDC::CreateEnhanced  
 Vytvoří kontext zařízení pro metasoubor rozšířeného formátu.  
  
```  
BOOL CreateEnhanced(
    CDC* pDCRef,  
    LPCTSTR lpszFileName,  
    LPCRECT lpBounds,  
    LPCTSTR lpszDescription);
```  
  
### <a name="parameters"></a>Parametry  
 *pDCRef*  
 Identifikuje odkazovacího zařízení pro rozšířený metasoubor.  
  
 *lpszFileName*  
 Odkazuje na řetězec znaků zakončené znakem null. Určuje název souboru pro rozšířený metasoubor, který se má vytvořit. Pokud má parametr hodnotu NULL, je rozšířený metasoubor paměti na základě a její obsah, mimo jiné ušlých při zničení objektu, nebo když Win32 `DeleteEnhMetaFile` funkce je volána.  
  
 *lpBounds*  
 Odkazuje [RECT](../../mfc/reference/rect-structure1.md) datová struktura nebo [crect –](../../atl-mfc-shared/reference/crect-class.md) objekt, který určuje rozměry v jednotkách HIMETRIC (v přírůstcích po.01 milimetru) obrázku, který bude uložen do rozšířený metasoubor.  
  
 *lpszDescription*  
 Odkazuje na řetězec ukončit nulou, který určuje název aplikace, která vytvoří na obrázku, stejně jako na obrázku názvu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Popisovač kontextu zařízení pro rozšířený metasoubor, v případě úspěchu; v opačném případě hodnota NULL.  
  
### <a name="remarks"></a>Poznámky  
 Tento řadič domény je možné uložit obrázek nezávislých na zařízení.  
  
 Windows používá odkazovacího zařízení identifikován *pDCRef* parametr řešení a jednotky zařízení původně zobrazeny obrázku. Pokud *pDCRef* parametr hodnotu NULL, použije aktuální zobrazovací zařízení pro referenci.  
  
 Členové levém a horním `RECT` datová struktura na které odkazují *lpBounds* parametr musí být menší než členů vpravo a dole v uvedeném pořadí. Na obrázku jsou zahrnuty body okraje obdélníku. Pokud *lpBounds* má hodnotu NULL, rozhraní grafiky zařízení (GDI) vypočítá dimenze nejmenší obdélník, který je možné uzavřít do uvozovek na obrázku vykreslena aplikací. *LpBounds* by měl být uveden parametr, kde je to možné.  
  
 Řetězec s odkazem *lpszDescription* parametr musí obsahovat prázdný znak mezi název aplikace a název obrázku a musí končit dva znaky s hodnotou null, například "XYZ grafiky Editor\0Bald Eagle\0\0, "kde \0 představuje znak null. Pokud *lpszDescription* má hodnotu NULL, neexistuje žádný odpovídající položku v záhlaví enhanced metafile.  
  
 Aplikace používají k ukládání obrázků grafiky v rozšířený metasoubor řadič domény vytvořené touto funkcí. Popisovač identifikující tento řadič domény je předat všechny funkce rozhraní GDI.  
  
 Po aplikaci uloží obrázek rozšířený metasoubor, může zobrazit obrázek na libovolném zařízení výstup voláním `CDC::PlayMetaFile` funkce. Při zobrazení obrázku Windows používá obdélníku, na které odkazují *lpBounds* parametr a data řešení z odkazovacího zařízení pro nastavení pozice a velikost obrázku. Kontext zařízení vrácená touto funkcí obsahuje stejnou výchozí atributy přidružené k žádné nový řadič domény.  
  
 Aplikace musí používat Win32 `GetWinMetaFileBits` funkce pro převod rozšířený metasoubor na dřívější formát Windows metafile.  
  
 Název souboru pro rozšířený metasoubor používejte. EMF rozšíření.  
  
## <a name="see-also"></a>Viz také  
 [CDC – třída](../../mfc/reference/cdc-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)



