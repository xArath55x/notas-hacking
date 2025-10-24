We made a lot of substitutions to encrypt this. Can you decrypt it? Connect with `nc jupiter.challenges.picoctf.org 13758`.

Hints:
	Flag is not in the usual flag format

# Solucion
Al conectarnos nos da esto:
```
┌──(diego㉿Tallin)-[~/pico/Crypto-parte1]
└─$ nc jupiter.challenges.picoctf.org 13758 
-------------------------------------------------------------------------------
fbopycek isys wk qbty hgcp - hysrtsofq_wk_f_bzsy_gcxjlc_lozehyecqt
-------------------------------------------------------------------------------
jseasso tk eisys ack, ck w iczs cgysclq kcwl kbxsaisys, eis jbol bh eis ksc. jskwlsk ibglwop bty iscyek ebpseisy eiybtpi gbop dsywblk bh ksdcycewbo, we icl eis shhsfe bh xcnwop tk ebgsycoe bh scfi beisy'k qcyokcol szso fbozwfewbok. eis gcaqsyeis jske bh bgl hsggbakicl, jsfctks bh iwk xcoq qscyk col xcoq zwyetsk, eis bogq ftkiwbo bo lsfn, col ack gqwop bo eis bogq ytp. eis cffbtoecoe icl jybtpie bte cgysclq c jbv bh lbxwobsk, col ack ebqwop cyfiwesfetycggq awei eis jbosk. xcygba kce fybkk-gsppsl ywpie che, gscowop cpcwoke eis xwmmso-xcke. is icl ktonso fissnk, c qsggba fbxdgsvwbo, c keycwpie jcfn, co ckfsewf ckdsfe, col, awei iwk cyxk lybddsl, eis dcgxk bh icolk bteacylk, ysksxjgsl co wlbg. eis lwysfeby, kcewkhwsl eis cofiby icl pbbl ibgl, xcls iwk acq che col kce lbao cxbopke tk. as svficopsl c hsa abylk gcmwgq. chesyacylk eisys ack kwgsofs bo jbcyl eis qcfie. hby kbxs ysckbo by beisy as lwl obe jspwo eice pcxs bh lbxwobsk. as hsge xslwecewzs, col hwe hby obeiwop jte dgcfwl kecywop. eis lcq ack solwop wo c ksysoweq bh kewgg col svrtwkwes jywggwcofs. eis acesy kibos dcfwhwfcggq; eis knq, aweibte c kdsfn, ack c jsowpo wxxsokweq bh tokecwosl gwpie; eis zsyq xwke bo eis skksv xcyki ack gwns c pctmq col yclwcoe hcjywf, itop hybx eis abblsl ywksk wogcol, col lycdwop eis gba kibysk wo lwcdicobtk hbglk. bogq eis pgbbx eb eis aske, jybblwop bzsy eis tddsy yscfisk, jsfcxs xbys kbxjys szsyq xwotes, ck wh copsysl jq eis cddybcfi bh eis kto.
```
Se puede probar con ROT13, vigenere pero vemos que no, despues podemos ver que se puede decodificar con cifrado por sustitucion, como el cesar o vigenere pero distinto. Tambien es suceptible a analisis de repeticiones
Podemos usar una pagina que haga este trabajo de romper el cifrado por substitucion 
https://www.guballa.de/substitution-solver
Donde nos dice como se mapeaban los alfabetos
```
abcdefghijklmnopqrstuvwxyz     This clear text ...  
woaptclfhbsdzkngyqeujximrv     ... maps to this cipher text
```
Con esto ya podemos ver el texto en claro y la flag
```
congrats here is your flag - frequency_is_c_over_lambda_dnvtfrtayu
-------------------------------------------------------------------------------
between us there was, as i have already said somewhere, the bond of the sea. besides holding our hearts together through long periods of separation, it had the effect of making us tolerant of each other's yarnsand even convictions. the lawyerthe best of old fellowshad, because of his many years and many virtues, the only cushion on deck, and was lying on the only rug. the accountant had brought out already a box of dominoes, and was toying architecturally with the bones. marlow sat cross-legged right aft, leaning against the mizzen-mast. he had sunken cheeks, a yellow complexion, a straight back, an ascetic aspect, and, with his arms dropped, the palms of hands outwards, resembled an idol. the director, satisfied the anchor had good hold, made his way aft and sat down amongst us. we exchanged a few words lazily. afterwards there was silence on board the yacht. for some reason or other we did not begin that game of dominoes. we felt meditative, and fit for nothing but placid staring. the day was ending in a serenity of still and exquisite brilliance. the water shone pacifically; the sky, without a speck, was a benign immensity of unstained light; the very mist on the essex marsh was like a gauzy and radiant fabric, hung from the wooded rises inland, and draping the low shores in diaphanous folds. only the gloom to the west, brooding over the upper reaches, became more sombre every minute, as if angered by the approach of the sun.
```