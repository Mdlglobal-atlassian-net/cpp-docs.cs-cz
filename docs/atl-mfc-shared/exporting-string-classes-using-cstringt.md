---
title: Export tříd řetězců pomocí CStringT | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- CStringT class, exporting strings
ms.assetid: bdfc441e-8d2a-461c-9885-46178066c09f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e7a4e033ac940d414cb3ece11dfd927b8c2658f7
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43762558"
---
# <a name="exporting-string-classes-using-cstringt"></a>Export tříd řetězců pomocí CStringT

V minulosti, mají vývojáři MFC odvozené od `CString` se specializují vlastních tříd řetězců. V rozhraní .NET aplikace Microsoft Visual C++ (MFC 8.0) [CString](../atl-mfc-shared/using-cstring.md) třídy byla nahrazena třídu šablony s názvem [CStringT](../atl-mfc-shared/reference/cstringt-class.md). To poskytuje několik výhod:

- Povolené MFC `CString` třída se používá v ATL projekty bez propojení v větší statické knihovny MFC nebo knihovny DLL.

- S novými `CStringT` třída šablony, můžete přizpůsobit `CString` chování pomocí parametrů šablony, které určují vlastnosti znaků, podobný šablony ve standardní knihovně jazyka C++.

- Při exportu vlastní řetězcové třídy z knihovny DLL pomocí `CStringT`, kompilátor také automaticky vyexportuje `CString` základní třídy. Protože `CString` samotného je třída šablony, může být vytvořena pomocí kompilátoru při použití, pokud kompilátor si je vědoma, který `CString` je importována z knihovny DLL. Pokud jste migrovali projekty Visual C++ 6.0 na Visual C++ .NET, možná jste viděli chybami linkeru symbolů pro násobení definovanou `CString` z důvodu kolize z `CString` naimportované z knihovny DLL a verze místní instance. Správný způsob, jak k tomu je popsána níže. Další informace o tomto problému najdete v článku znalostní báze Knowledge Base "propojení chyb při importu CString odvozené třídy" (Q309801) na [ http://support.microsoft.com/default.aspx ](http://support.microsoft.com/default.aspx).

Následující příklad způsobí, že linkeru, aby způsobí chyby symbol pro vícenásobně definovaný třídy. Předpokládejme, že exportujete `CString`-odvozené třídy (`CMyString`) z rozšiřující knihovny DLL MFC:

[!code-cpp[NVC_MFC_DLL#6](../atl-mfc-shared/codesnippet/cpp/exporting-string-classes-using-cstringt_1.cpp)]

Uživatelský kód používá kombinaci `CString` a `CMyString`. "MyString.h" není součástí předkompilované hlavičky a některé využití `CString` nemá `CMyString` viditelné.

Předpokládejme, že používáte `CString` a `CMyString` třídy v samostatných zdrojové soubory, Source1.cpp a Source2.cpp. V Source1.cpp, použijete `CMyString` a #include MyString.h. V Source2.cpp, použijete `CString`, ale ne #include MyString.h. V takovém případě bude stěžují propojovací program `CStringT` je definovaná víckrát. To je způsobeno `CString` se obě naimportované z knihovny DLL, který exportuje `CMyString`a vytvořit instanci místně pomocí kompilátoru prostřednictvím `CStringT` šablony.

Chcete-li tento problém vyřešit, postupujte takto:

Export `CStringA` a `CStringW` (a potřebné základní třídy) z MFC90. KNIHOVNY DLL. Projekty, které zahrnují MFC bude vždy používat knihovnu MFC DLL exportovat `CStringA` a `CStringW`, jako v předchozích implementacích knihovny MFC.

Pak vytvořte exportovatelné odvozené třídy pomocí `CStringT` šablony, jako `CStringT_Exported` je menší než, například:

[!code-cpp[NVC_MFC_DLL#7](../atl-mfc-shared/codesnippet/cpp/exporting-string-classes-using-cstringt_2.cpp)]

V AfxStr.h, nahraďte předchozí `CString`, `CStringA`, a `CStringW` – definice TypeDef následujícím způsobem:

[!code-cpp[NVC_MFC_DLL#8](../atl-mfc-shared/codesnippet/cpp/exporting-string-classes-using-cstringt_3.cpp)]

Existuje několik omezení:

- Neexportujte `CStringT` samotný protože to způsobí, že projekty jen knihovny ATL pro export specializovaný `CStringT` třídy.

- Pomocí exportovatelné odvozené třídy z `CStringT` minimalizuje museli znova implementovat `CStringT` funkce. Další kód je omezen na předávání pro konstruktory `CStringT` základní třídy.

- `CString`, `CStringA`, a `CStringW` pouze by měla být označena `__declspec(dllexport/dllimport)` při vytváření pomocí knihovny MFC sdílené knihovny DLL. Propojení s statické knihovny MFC, by neměla označíte-li tyto třídy exportovat, v opačném případě interní použití `CString`, `CStringA`, a `CStringW` uvnitř knihovny DLL uživatele označí `CString` také exportovat.

## <a name="related-topics"></a>Související témata

[CStringT – třída](../atl-mfc-shared/reference/cstringt-class.md)

## <a name="see-also"></a>Viz také

[Cstringt – použití](../atl-mfc-shared/using-cstringt.md)   
[CString – použití](../atl-mfc-shared/using-cstring.md)

