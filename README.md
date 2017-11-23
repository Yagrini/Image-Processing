# Image-Processing

## int seuillage_otsu(vector<int> histo) ;
 Fonction qui prend en paramètre l'histogramme d'une image et
renvoie un entier qui est le seuil obtenu avec la méthode
d’Otsu pour cette image.
## double** calculNoyauGaussien(int s) ;
La fonction prend les arguments suivants :
s : le rayon du noyau. Le noyau sera donc une matrice d’une taille (s*2+1)* (s*2+1).
Cette fonction retourne une matrice qui représente le noyau Gaussien et dont les différentes cases ont des valeurs calculés à l’aide de la distribution gaussienne standard.
## Mat lissageGaussien(Mat &img ,int  s=1) ;
La fonction prend les arguments suivants :
img : l’image qu’on veut lisser (réduire le bruit) avec un
lissage gaussien.
s : le rayon du noyau gaussien, par défaut égale à 1.
Cette fonction permet pour chaque pixel centré de la zone sur
laquelle il s'applique le noyau gaussien, de modifier sa
valeur en fonction des valeurs des pixels avoisinants,
affectées aux coefficients du noyau.
Output : Image résultante de même taille que celle en entrée. Les valeurs des pixels de cette image sont ceux de l’image originale après l’application du noyau gaussien.
## Mat lissageMedian(Mat &img,int r=1);
La fonction prend les arguments suivants :
img : l’image qu’on veut lisser (réduire le bruit) avec un lissage Median.
r : le rayon du voisinage d’un pixel, par défaut égale à 1.
Output : Image résultante de même taille que celle en entrée. La valeur de chaque pixel de cette image reçoit la valeur médiane du voisinage de pixel correspondant dans l’image originale.
## Mat FiltreMedian(Mat& img, int r=1) ;
Les mêmes arguments que la fonction précédente sauf que dans cette fonction on fait la différence entre deux cas.
Si l’image est en gris on retourne directement la fonction précédente.
    
Sinon, on sépare l’image en 3 images (une contenant les valeurs de rouge, une contenant les valeurs du bleu et une contenant les valeurs du vert). Après, on applique la fonction précédente pour chacune de ces images et finalement on fusionne ces images et on retourne l’image lissée avec un lissage médian.
## Mat FiltreMoyenneur(Mat& src, int r=1 ) ;
La fonction prend les arguments suivants :
img : l’image qu’on veut lisser (réduire le bruit) avec un lissage Moyenneur.
r : le rayon du voisinage d’un pixel, par défaut égale à 1.
Output : Image résultante de même taille que celle en entrée. La valeur de chaque pixel de cette image reçoit la valeur moyenne des valeurs des pixels du voisinage de pixel correspondant dans l’image originale.
## Mat contourGradient(Mat img , int MasqueX[3][3] , int MasqueY[3][3]) ;
La fonction prend les arguments suivants :
img : l’image sur laquelle on veut appliquer le contour du gradient.
MasqueX : le masque convenable qui mesure la variation de la valeur du pixel par rapport à la direction horizontale. MasqueY : le masque qui mesure la variation de la valeur du pixel par rapport à la direction verticale.
Si l’image en entrée est en couleur on la convertit en gris. Pour toutes les zones de l’image :
On applique le MasqueX.
On applique le MasqueY.
On calcule le gradient pour le pixel qui présente le centre de la zone à l’aide de la relation |G|=sqrt(MasqueX2 + MasqueY2).
Output : image résultante de même taille que celle originale contient les points de bords de l’image en entrée.
L’application des Masques se fait à l’aide de la fonction :
## int Calcul(Mat& img, int x , int y , int Masque[3][3]) ;
La fonction prend les arguments suivants :
Img : l’image sur laquelle on veut appliquer le Masque .
x : la position horizontale du pixel qui présente le centre de la zone sur laquelle on veut appliquer le Masque.
y : la position verticale du pixel qui présente le centre de la zone sur laquelle on veut appliquer le Masque.
    
Masque[3][3] : Le masque que l’on veut appliquer.
Mat contourCanny(Mat img) ;
La fonction prend les arguments suivants :
img : l’image sur laquelle on veut appliquer le contour du
canny.
Après le calcul de la variation de la valeur de chaque pixel par rapport à la direction horizontale et verticale, on détermine l’orientation du bord pour chaque pixel et par suite on détermine les deux voisins appartenant au bord passant par ce pixel.
Output : image résultante de même taille que celle originale
contient les points de bords qui présentent un maximum local
dans son voisin.
## Mat contourLaplacien(Mat img , int S) ;
La fonction prend les arguments suivants :
img : l’image sur laquelle on veut appliquer le contour de Laplace.
S : un seuil qui a par défaut la valeur du seuil obtenu avec la méthode d’Otsu sur l’image passée en paramètre .
On applique d’abord le masque de Laplace sur l’image (il s’agit de la 2ème dérivée), après on considère toute les zone de taille 3*3 de l’image. Si le centre de la zone s’agit un passage à zéro on compare sa variance locale au seuil S si le seuil S dépasse la variance locale, on déclare un bord.
Output : image résultante de même taille que celle originale contient les points de bords déterminés à l’aide du contour de Laplace.
## Mat Seuillage(Mat img , int seuil) ;
La fonction prend les arguments suivants :
img : l’image sur laquelle on veut appliquer le contour du canny.
seuil : un seuil qui a par défaut la valeur du seuil obtenu avec la méthode d’Otsu sur l’image passée en paramètre .
si l’image en couleur on la convertit en gris.
   
Output : image résultante de même taille que celle originale. Si dans l’image originale la valeur d’un pixel est supérieure au seuil ou le pixel est lié à un pixel dont la valeur est supérieure au seuil alors la valeur de ce pixel est conservée dans l’image résultante, sinon elle est mise à zéro dans l’image résultante.
## vector<int> CalculHist(Mat image) ;
La fonction prend les arguments suivants :
img : image en gris pour la quelle on veut calculer le
histogramme.
Output : un vecteur de longueur 256 et qui contient le nombre d’occurrence de chaque valeur appartenant à l’intervalle [0- 255] dans l’image.
## vector<int> CalculHistNeg(Mat& image) ;
La fonction prend les arguments suivants :
img : image en gris pour la quelle on veut calculer le
histogramme négatif.
Output : un vecteur de longueur 256 symétrique au vecteur qui présente l’histogramme de l’image par rapport à la droite d’équation x=127.
## vector<int> CalculHist(Mat& image, int x) ;
La fonction prend les arguments suivants :
img : image en gris pour la quelle on veut calculer le
histogramme.
x : entier égale à 0 ou à 1 ou à 2, c’est à dire c’est l’image
qui représente les valeurs du bleu ou bien du rouge ou bien du
vert dans l’image originale.
Output : un vecteur de longueur 256 et qui contient le nombre d’occurrence de chaque valeur appartenant à l’intervalle [0- 255] dans l’image.
## vector<int> CalculHistNeg(Mat& image, int x) ;
La fonction prend les arguments suivants :
img : image en gris pour la quelle on veut calculer le
histogramme négatif.
x : entier égale à 0 ou à 1 ou à 2, c’est à dire c’est l’image
qui représente les valeurs du bleu ou bien du rouge ou bien du
vert dans l’image originale.
    
Output : un vecteur de longueur 256 symétrique au vecteur qui présente l’histogramme de l’image par rapport à la droite d’équation x=127.
## Mat Histogramme(Mat image) ;
La fonction prend les arguments suivants :
img : l’image pour laquelle on veut dessiner le histogramme.
Si l’image est on gris alors:
Output une image contenant une courbe qui représente le vecteur histogramme obtenu à l’aide de la fonctions vector<int> CalculHistNeg(Mat& image) ;
Sinon alors:
Output  une image contenant trois courbe. Chacune d’eux
représente le vecteur histogramme obtenu à l’aide de la
fonction vector<int> CalculHist(Mat& image, int x) ;  avec la
couleur associée.
## Mat HistogrammeNegatif(Mat image) ;
La fonction prend les arguments suivants :
img : l’image pour laquelle on veut dessiner le histogramme.
 Si l’image est on gris alors:
Output  une image contenant une courbe qui représente le
vecteur histogramme obtenu à l’aide de la fonctions
## vector<int> CalculHistNeg(Mat& image) ;
Sinon alors:
Output : une image contenant trois courbe. Chacune d’eux représente le vecteur histogramme obtenu à l’aide de la fonction vector<int> CalculHistNeg(Mat& image, int x) ; avec la couleur associée.
inline uchar reduire(int n) ;
Fonction utilisée dans les ajouts de bruits pour avoir toujours des pixels dont les valeurs ne dépassent pas 0 et 255.
Mat Ajouter_bruit_gaussien(cv::Mat src,float moyenne,float
ecart_type);
Cette fonction prend en entrée 3 paramètres :
Le premier évidement sera notre image source.
      
Le deuxième sera le premier paramètre de la distribution
gaussienne (la moyenne).
Le troisième sera le deuxième paramètre de la distribution
gaussienne (l'écart-type)
On teste tout d'abord si l'image est en niveaux de gris ou en RGB (les traitements seront presque les mêmes pour les deux cas)
On remplit une matrice avec le bruit qui sera généré aléatoirement par une distribution gaussienne puis en ajoute cette dernière a notre image source tout en tenant compte que nos pixels ne doivent pas les valeurs 0 et 255.
## Mat Ajouter_bruit_uniforme(cv::Mat src,float mini,float maxi) ;
Cette fonction prend en entrée 3 paramètres :
Le premier sera notre image source.
Le 2éme et le 3éme seront les paramètres de la distribution uniforme (min et max).
Ce sera bien sur le même traitement que celui de la
distribution gaussienne, la seul différence sera la génération
du bruit par une distribution uniforme.
## Mat Ajouter_bruit_sel_poivre(cv::Mat src,float poivre,float sel) ;
Cette fonction prend en entrée 3 paramètres :
Le premier sera notre image source.
Le deuxième sera la quantité de poivre entre 0 et 255.
Le troisième sera la quantité de sel entre 0 et 255.
On génère une copie de l'image source puis on met des pixels 0
(respectivement 255) aléatoirement par une distribution
uniforme.
## Mat dessiner_histogramme(cv::Mat src) ;
Un seul paramètre sera passé a l'appel de cette fonction qui
sera bien sur l'image source.
Le traitement vérifie d'abord si l'image est en niveaux de
gris ou RGB.
On sépare d'abord les canaux RGB de l'image puis pour chaque canal on calcule l'histogramme qui sera mis dans le vecteur qui sera par la suite dessiné en reliant chaque 2 points successifs par une ligne.
     
Avant de dessiner bien sur l'histogramme une normalisation du vecteur sera nécessaire puisque les valeurs de l'histogramme peuvent avoir une très grande variance, dans cette implémentation on utilise la norme min max pour normaliser notre histogramme.
## Mat dessiner_negatif_histogramme(cv::Mat src) ;
Le seul paramètre passé sera l'image source.
On appelle la fonction de dessin d'histogramme mais en lui
passant comme source le négatif de l'image passé en paramètre.
Mat niveaux_de_gris(cv::Mat src) ;
Cette fonction transforme une image RGB en gris .
## Mat equalization_histogramme(cv::Mat src) ;
Égalisation de l'histogramme:
Un seul paramètre : image source.
On passe du RGB au YCrCb et on divise les canaux Y et Cr et Cb
puisque l'égalisation doit être faite sur le canal Y de la
luminance.
On mélange les 3 canaux et on reconverti notre image à la base
RGB.
## Mat binarisation(int seuil,cv::Mat src) ;
Fonction qui prend en argument un seuil et l'image source puis
renvoie une image binarisée.
## Mat binarisation_otsu(Mat src) ;
Binarisation qui se base sur un seuil trouvé par la méthode d’Otsu.
## Mat segmenter_image(Mat src,int k) ;
Cette fonction prend en paramètre l'image source et un entier
K.
Le traitement est le suivant :
On cherche les K pixels les plus dominant dans l'image en
      
utilisant la méthode des K-moyennes et on redessine notre
image en utilisant seulement ces K couleurs
N.B : Cette fonction et après maintes optimisations prend un temps considérable pour s'exécuter en fonction du nombre de couleurs K de le segmentation et la taille de l'image.
## vector<int> encode_RLE(vector<int> str) ;
Prend un vecteur en entrée et renvoie son encodage RLE en
vecteur.
## vector<int> decode_RLE(vector<int>  str) ;
Décodage RLE.
## Mat calculDCT(cv::Mat oo) ;
Calcul de la transformée en cosinus discrète d'un bloc d'image
de taille 8x8.
## Mat calculiDCT(cv::Mat oo) ;
Calcul de la transformée en cosinus discrète inverse d'un bloc
d'image de taille 8x8.
## Mat compression_dct(cv::Mat src) ;
Prend en paramètre une image source et renvoie une image avec
une qualité réduite simulant une compression puis
décompression DCT d'une image jpeg en prenant en compte si
l'image est en RGB ou niveau de gris.
## COMPRESSION HUFFMAN
Définission de l’arbre utilisé dans la compression Huffman :
struct Arbre
{
    int val;
    int occ;
    Arbre *fd, *fg;
    Arbre(int valeur, int occurence)
    {
        fg = fd = NULL;
        this->val = valeur;
        
        this->occ = occurence;
    }
};
Définition de la structure utilisée pour la comparaison dans :priority_queue<Arbre*, vector<Arbre*>, comparer>
struct comparer
{
    bool operator()(Arbre* l, Arbre* r)
    {
        return (l->occ > r->occ);
    }
};
void HuffmanAr(vector<int> vect,priority_queue<Arbre*, vector<Arbre*>, comparer>& mafile) ;
La fonction prend les arguments suivants :
vect : un vecteur d’entiers.
mafile : priority queue pour stocker le tas, par rapport à la valeur du nœud racine.
Cette fonction permet de construire l’arbre de Huffman et le stocker dans mafile.
void HuffmanArbre(Mat & image,priority_queue<Arbre*, vector<Arbre*>, comparer>& mafile) ;
La fonction prend les arguments suivants :
image : image en gris.
mafile : priority queue pour stocker le tas, par rapport à la valeur du nœud racine.
On calcule d’abord un vecteur d’histogramme de l’image nommé resultat. Puis on appelle la fonction HuffmanAr(resultat,mafile).
Cette fonction permet de déterminer l’arbre de Huffman pour une image en gris.
void codage(struct Arbre* monarbre, string
str,vector<string> & vect) ;
La fonction prend les arguments suivants :
monarbre : arbre de Huffman.
str : une chaine de caractère vide pour faciliter la lecture.
           
vect :  un vecteur de longueur 256 contient des chaines de
caractères .
Cette fonction permet de la lecture de l’arbre de Huffman et pour chaque indice du vecteur vect il sera stocké le code associé.
string CodageHuffmanseulniveau(Mat image,priority_queue<Arbre*, vector<Arbre*>, comparer> & file) ;
La fonction prend les arguments suivants :
image : image en gris.
file : priority queue pour stocker le tas, par rapport à la valeur du nœud racine.
Dans cette fonction on fait appel aux fonctions HuffmanArbre(image,file);
et codage(file.top(), "" , resultat);
et à partir du vecteur resultat et en circulant l’image originale pixel par pixel on détermine le code Huffman de cette image .
Output : une chaine de caractères contenant le code Huffman et
la longueur et la largeur de l’image originale.
vector<string> CodageHuffman(Mat image,priority_queue<Arbre*, vector<Arbre*>, comparer> & file,priority_queue<Arbre*, vector<Arbre*>, comparer> & file1=mafile1,priority_queue<Arbre*, vector<Arbre*>, comparer> & file2= mafile2) ;
La fonction prend les arguments suivants :
image : image originale.
file : priority queue pour stocker le tas, par rapport à la valeur du nœud racine.
file1 : priority queue pour stocker le tas, par rapport à la valeur du nœud racine.
file2 : priority queue pour stocker le tas, par rapport à la valeur du nœud racine.
file2 et file3 sont utilisés pour le cas d’une image en couleur.
Si l’image en gris alors :
Output : un vecteur de string contient le code Huffman de l’image.
        
Sinon : On sépare l’image en 3 images (une contenant les valeurs de rouge, une contenant les valeurs du bleu et une contenant les valeurs du vert). Après, on applique la fonction CodageHuffmanseulniveau pour chacune de ces images
Output : un vecteur de string contenant trois codes Huffman pour chaque les trois niveaux de couleur de l’image.
Mat DecodageHuffmanunniveau(string Huffmancode,struct Arbre* Ar) :
La fonction prend les arguments suivants :
Huffmancode : Le code Huffmane.
Ar : L’arbre Huffman.
Output : image résultante obtenue après la lecture du code
Huffman à l’aide de l’arbre Huffman.
Mat DecodageHuffman(vector<string> Huffmancode,struct Arbre* Arbre1 , struct Arbre* Arbre2 = Ar1, struct Arbre* Arbre3 = Ar1) ;
La fonction prend les arguments suivants :
Huffmancode : code Huffmane.
Arbre1: arbre Huffman
Arbre2: arbre Huffman
Arbre3: arbre Huffman
Arbre2 et Arbre3 sont utilisés pour le cas d’une image en couleur.
Si l’image en gris alors :
Output : image résultante obtenue après la lecture du code
Huffman à l’aide de l’arbre Huffman en appelant la fonction
DecodageHuffmanunniveau(Huffmancode[0],Arbre1);
Sinon : On applique la fonction DecodageHuffmanunniveau pour chacun de ces code et ces arbres. On obtient l’image résultante de chaque niveau de couleur (bleu, rouge et vert) puis on les fusionne dans l’image résultante.
Output : image en couleur résultante obtenue après la lecture
du code Huffman à l’aide des arbre Huffman.
