---
ms.openlocfilehash: bf83723de025f3e1f6bde5b4226fc8966dff6b9a
ms.sourcegitcommit: 64947f11d367ffbebbafb700fdfdc20617275f35
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "48829664"
---
<!-- markdownlint-disable MD002 MD041 -->

<span data-ttu-id="edf9a-101">L’étape de configuration finale permettant de s’assurer que le connecteur est prêt à être utilisé est d’autoriser et de tester le connecteur personnalisé afin de créer une connexion mise en cache.</span><span class="sxs-lookup"><span data-stu-id="edf9a-101">The final configuration step to ensure the connector is ready for use is to authorize and test the custom connector to create a cached connection.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="edf9a-102">Pour suivre les étapes suivantes, vous devez être connecté avec des privilèges d’administrateur.</span><span class="sxs-lookup"><span data-stu-id="edf9a-102">The following steps requires that you are logged in with administrator privileges.</span></span>

<span data-ttu-id="edf9a-103">Dans [Microsoft Power automate](https://flow.microsoft.com), accédez à l’élément de menu **données** à gauche et choisissez la page **connexions** .</span><span class="sxs-lookup"><span data-stu-id="edf9a-103">In [Microsoft Power Automate](https://flow.microsoft.com), go to the **Data** menu item on the left and choose the **Connections** page.</span></span> <span data-ttu-id="edf9a-104">Sélectionnez le lien **nouvelle connexion** .</span><span class="sxs-lookup"><span data-stu-id="edf9a-104">Choose the **New Connection** link.</span></span>

![Capture d’écran du bouton nouvelle connexion](./images/new-connection.png)

<span data-ttu-id="edf9a-106">Recherchez votre connecteur personnalisé et terminez la connexion en cliquant sur le bouton plus.</span><span class="sxs-lookup"><span data-stu-id="edf9a-106">Find your custom connector and complete the connection by clicking the plus button.</span></span> <span data-ttu-id="edf9a-107">Connectez-vous à l’aide de votre compte Azure Active Directory de l’administrateur client Office 365.</span><span class="sxs-lookup"><span data-stu-id="edf9a-107">Sign in with your Office 365 tenant administrator's Azure Active Directory account.</span></span>

![Capture d’écran de la liste connexions](./images/connection-sign-in.png)

<span data-ttu-id="edf9a-109">Lorsque vous êtes invité à entrer les autorisations demandées, vérifiez le **consentement au nom de votre organisation** , puis choisissez **accepter** pour autoriser les autorisations.</span><span class="sxs-lookup"><span data-stu-id="edf9a-109">When prompted for the requested permissions, check **Consent on behalf of your organization** and then choose **Accept** to authorize permissions.</span></span>

![Capture d’écran de l’invite de consentement](./images/consent-prompt.png)

<span data-ttu-id="edf9a-111">Une fois que vous avez autorisé les autorisations, une connexion est créée dans Power automate.</span><span class="sxs-lookup"><span data-stu-id="edf9a-111">After you authorize the permissions, a connection is created in Power Automate.</span></span>

<span data-ttu-id="edf9a-112">Le connecteur personnalisé est maintenant configuré et activé.</span><span class="sxs-lookup"><span data-stu-id="edf9a-112">The custom connector is now configured and enabled.</span></span> <span data-ttu-id="edf9a-113">Il peut y avoir un retard dans les autorisations appliquées et disponibles, mais le connecteur est maintenant configuré.</span><span class="sxs-lookup"><span data-stu-id="edf9a-113">There may be a delay in permissions being applied and available, but the connector is now configured.</span></span>
