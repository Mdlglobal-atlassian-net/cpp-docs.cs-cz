---
title: "Konvence vytváření názvů pro knihovny MFC DLL | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- MFC libraries [C++], naming conventions
- naming conventions [C++], MFC DLLs
- MFC DLLs [C++], naming conventions
- libraries [C++], MFC DLL names
- shared DLL versions [C++]
- DLLs [C++], naming conventions
- DLLs [C++], library names
ms.assetid: 0db9c3f3-87d3-40e8-8964-250f9d2a2209
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 4f7702e9babcc4769136d6deab63b627f8b09bd4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="naming-conventions-for-mfc-dlls"></a>Zásady vytváření názvů pro knihovny MFC DLL
Knihovny DLL a knihovny zahrnuty v MFC podle strukturované zásady vytváření názvů. To usnadňuje vědět, které knihovny DLL nebo knihovna by měl použít pro konkrétní účel.  
  
 Importované knihovny potřebné k vytváření aplikací nebo MFC DLL rozšíření, které používají tyto knihovny DLL mají stejné základní název jako knihovny DLL ale mít příponu názvu souboru LIB.  
  
### <a name="shared-dll-naming-convention"></a>Zásady vytváření názvů sdílenou knihovnu DLL.  
  
|DLL|Popis|  
|---------|-----------------|  
|MFCx0.DLL|MFC DLL ANSI prodejní verzi|  
|MFCx0U.DLL|MFC DLL, Unicode prodejní verzi|  
|Verze knihovny MFCx0D.DLL|MFC DLL verze ANSI ladění|  
|MFCx0UD.DLL|MFC DLL, Unicode ladicí verze|  
  
 Pokud vytváříte dynamicky propojení sdílenou knihovnu DLL verze knihovny MFC, zda je z aplikace nebo knihovnu DLL, musíte zahrnout MFCx0.DLL s produktem. Pokud budete potřebovat Podpora kódování Unicode v aplikaci, zahrnují MFCx0U.DLL.  
  
 Pokud vaše knihovna DLL staticky propojujete s knihovnou MFC, je nutné ji s jedním z statické knihovny MFC propojit. Tyto verze jsou pojmenované podle konvence [N &#124; U] AFXCW [D]. LIB. Další informace najdete v tabulce "Staticky propojené zásady vytváření názvů knihoven" v [zásady vytváření názvů knihoven](../mfc/library-naming-conventions.md) (MFC).  
  
 Seznam Visual C++ knihovny DLL, které můžete distribuovat s vašimi aplikacemi najdete v souboru Redist.txt v instalaci sady Visual Studio.  
  
## <a name="what-do-you-want-to-know-more-about"></a>Co chcete vědět více o?  
  
-   [Zásady vytváření názvů pro knihovny](../mfc/library-naming-conventions.md)  
  
## <a name="see-also"></a>Viz také  
 [Knihovny DLL v jazyce Visual C++](../build/dlls-in-visual-cpp.md)