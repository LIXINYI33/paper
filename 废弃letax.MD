
	建立广义线性模型，因变量为Y染色体浓度，自变量为年龄，身高，体重，IVF妊娠方式，检测孕周数，孕妇BMI，怀孕次数，
	生产次数。通过多重共线性判断，如果一个变量与其他变量具有高度相关性即可以被其他变量预测，那么将这个自变量加入
	模型会影响模型准确性。

	由辅助回归模型可知，分别将自变量视为因变量$X_{j}$,将其余所以自变量$X_{1},\ldots,X_{j-1},X_{j+1},\ldots,X_{k}$作
	为自变量进行线性回归。
	\begin{equation*}
		X_{j}=\beta _{0}+\beta _{1}X_{1}+\ldots +\beta _{j-1}X_{j-1}+\beta _{j+1}X_{j+1}+\ldots+\beta _{K}X_{k}+\epsilon 
	\end{equation*}
	求出辅助回归模型的判定系数$R_{j}^{2}$，$R_{j}^{2}$表示$X_{j}$与其他自变量相关性。$R_{j}^{2}$越接近1，相关性越强。


	\begin{equation*}
		VIF_{j}=\dfrac{1}{1-R_{j}^{2}}
	\end{equation*}




	\begin{table}[!ht]
		\centering
    	\setlength{\tabcolsep}{4pt} % 减少列间距
    	\setlength{\extrarowheight}{-1pt} % 减少行高
		\begin{tabular}{l|ll}
			\textbf{变量} & \textbf{VIF} & \textbf{1/VIF} \\ \hline
			年龄 & 1.09 & 0.917581 \\ 
			身高 & 107.5 & 0.009303 \\ 
			体重 & 353.81 & 0.002826 \\ 
			检测天数 & 1.03 & 0.973747 \\
			孕妇BMI & 220.2 & 0.004541 \\ 
			怀孕次数 & 1.71 & 0.586078 \\ 
			生产次数 & 1.66 & 0.601476 \\ 
			自然受孕 & ~ & ~ \\ 
			人工授精 & 1.03 & 0.974804 \\ 
			试管婴儿 & 1.04 & 0.957430 \\ \hline
			总VIF & 76.56 & ~ \\ 
		\end{tabular}
	\end{table}

	分析表格，发现身高和体重的VIF很大，证明



	\begin{table}[!ht]
    \centering
    \setlength{\tabcolsep}{4pt} % 减少列间距
    \setlength{\extrarowheight}{-1pt} % 减少行高
    \begin{tabular}{l|ll}
    
        \textbf{变量} & \textbf{VIF} & \textbf{1/VIF} \\ \hline
        年龄 & 1.08 & 0.925317 \\ 
        身高 & 1.02 & 0.981982 \\ 
        检测天数 & 1.03 & 0.973908 \\ 
        孕妇BMI & 1.05 & 0.953768 \\ 
        怀孕次数 & 1.71 & 0.586080  \\ 
        生产次数 & 1.66 & 0.603483 \\ 
        自然受孕 & ~ & ~ \\
        人工授精 & 1.03 & 0.975041 \\ 
        试管婴儿 & 1.04 & 0.958837 \\ 
        总VIF & 1.2 & ~ \\ 
    \end{tabular}
\end{table}




% 第一个表格转置
\begin{table}[!ht]
    \centering
    \scriptsize % 使用较小的字体
	\setlength{\tabcolsep}{5pt} % 减少列间距
    \begin{tabular}{lcccccccccc}
        \toprule
        & \textbf{年龄} & \textbf{身高} & \textbf{体重} & \textbf{检测天数} & \textbf{孕妇BMI} & \textbf{怀孕次数} & \textbf{生产次数} & \textbf{自然受孕} & \textbf{人工授精} & \textbf{试管婴儿} \\
        \midrule
        \textbf{VIF} & 1.09 & 107.5 & 353.81 & 1.03 & 220.2 & 1.71 & 1.66 & -- & 1.03 & 1.04  \\
        \textbf{1/VIF} & 0.917581 & 0.009303 & 0.002826 & 0.973747 & 0.004541 & 0.586078 & 0.601476 & -- & 0.974804 & 0.957430  \\
        \bottomrule
    \end{tabular}
    \caption{第一个表格的转置版本}
\end{table}

% 第二个表格转置
\begin{table}[!ht]
    \centering
    \scriptsize % 使用较小的字体
	\setlength{\tabcolsep}{5pt} % 减少列间距
    \begin{tabular}{lccccccccc}
        \toprule
        & \textbf{年龄} & \textbf{身高} & \textbf{检测天数} & \textbf{孕妇BMI} & \textbf{怀孕次数} & \textbf{生产次数} & \textbf{自然受孕} & \textbf{人工授精} & \textbf{试管婴儿} \\
        \midrule
        \textbf{VIF} & 1.08 & 1.02 & 1.03 & 1.05 & 1.71 & 1.66 & -- & 1.03 & 1.04  \\
        \textbf{1/VIF} & 0.925317 & 0.981982 & 0.973908 & 0.953768 & 0.586080 & 0.603483 & -- & 0.975041 & 0.958837  \\
        \bottomrule
    \end{tabular}
    \caption{第二个表格的转置版本}
\end{table}


\begin{table}
\begin{tabular}{lcccccc}
\toprule
解释变量 & \textbf{系数} & \textbf{标准误} & \textbf{统计量} & \textbf{P>|t|} & \textbf{[95\%置信区间]} \\
\midrule
\textbf{年龄\_z} & -0.0038288 & 0.0010249 & -3.74 & 0.000 & -0.0058398 & -0.0018178 \\
\textbf{身高\_z} & -0.002752 & 0.0009949 & -2.77 & 0.006 & -0.0047041 & -0.0007999 \\
\textbf{IVF妊娠 2} & 0.0151552 & 0.0109828 & 1.38 & 0.168 & -0.006395 & 0.0367054 \\
\textbf{IVF妊娠 3} & -0.0188821 & 0.0117415 & -1.61 & 0.108 & -0.0419211 & 0.0041569 \\
\textbf{检测孕周转换为天数\_z} & 0.0050617 & 0.000999 & 5.07 & 0.000 & 0.0031015 & 0.0070219 \\
\textbf{孕妇BMI\_z} & -0.0054842 & 0.0010095 & -5.43 & 0.000 & -0.007465 & -0.0035034 \\
\textbf{怀孕次数\_z} & 0.000018 & 0.0012878 & 0.01 & 0.989 & -0.0025089 & 0.0025448 \\
\textbf{生产次数\_z} & 0.0014426 & 0.0012691 & 1.14 & 0.256 & -0.0010476 & 0.0039327 \\
\textbf{常数项} & 0.0771624 & 0.0009935 & 77.66 & 0.000 & 0.0752129 & 0.0791119 \\
\bottomrule
\end{tabular}
\end{table}


\begin{table}[!ht]
\centering
\caption{回归分析结果}
\small
\begin{tabular}{lcccc}
\toprule
\textbf{变异来源} & \textbf{平方和} & \textbf{自由度} & \textbf{均方} \\
\midrule
Model & 0.087523861 & 8 & 0.010940483 \\
Residual & 1.12526182 & 1,072 & 0.001049685 \\
Total & 1.21278568 & 1,080 & 0.00112295 \\
\bottomrule
\end{tabular}
\end{table}



\begin{table}
\begin{tabular}{|l|l|}
\hline
样本量  & 1,081 \\
F(8, 1072)  & 10.42 \\
Prob > F  & 0.0000 \\
决定系数 & 0.0722 \\
调整决定系数 & 0.0652 \\
均方根误差 & 0.0324 \\  \hline
\end{tabular}	
\end{table}

	\begin{figure}[ht]
		\centering
		\subcaptionbox{孕妇状态和临床指标的相关系数矩阵\label{fig:双图a}}
		{\includegraphics[width=.45\textwidth]{figures/spearman1.png}}
		\hfill % 让两个子图尽可能分开
		\subcaptionbox{测序质量指标的相关系数矩阵\label{fig:双图b}}
		{\includegraphics[width=.45\textwidth]{figures/spearman2.png}}
		\caption{检测与临床指标相关系数分析矩阵}
		\label{fig:双图}
	\end{figure}


	\begin{figure}[ht]
		\centering
		\subcaptionbox{染色体相关指标的相关系数矩阵\label{fig:双图a}}
		{\includegraphics[width=.45\textwidth]{figures/spearman3.png}}
		\hfill % 让两个子图尽可能分开
		\subcaptionbox{Y染色体浓度的相关系数矩阵\label{fig:双图b}}
		{\includegraphics[width=.45\textwidth]{figures/spearman4.png}}
		\caption{染色体相关系数分析矩阵}
		\label{fig:双图}
	\end{figure}


	\begin{table}[H]
	\centering
	\caption{混淆矩阵}
	\label{tab:confusion_matrix}
		\begin{tabular}{|c|c|c|c|}
		\hline
		\multirow{2}{*}{实测 \textbackslash 预测} & \multicolumn{2}{c|}{预测类别} & \multirow{2}{*}{行总计} \\ \cline{2-3}
		& 正常 (0) & 异常 (1) & \\ \hline
		真实正常 (0) & 374 (TN) & 13 (FP) & 387 \\ \hline
		真实异常 (1) & 57 (FN) & 34 (TP) & 91 \\ \hline
		列总计 & 431 & 47 & 478 \\ \hline
		\end{tabular}
	\end{table}


	\begin{table}[H]
	\centering
	\caption{模型性能指标}
	\label{tab:performance_metrics}
		\begin{tabular}{|l|c|}
		\hline
		\multicolumn{1}{|c|}{指标} & 值 \\ \hline
		总体准确率 & 85.4\% \\ \hline
		敏感性（召回率） & 37.4\% \\ \hline
		特异性 & 96.6\% \\ \hline
		精确率 & 72.3\% \\ \hline
		\end{tabular}
	\end{table}


	\begin{table}[H]
	\centering
	\caption{混淆矩阵}
	\label{tab:confusion_matrix}
		\begin{tabular}{|c|c|c|c|}
		\hline
		\multirow{2}{*}{实测 \textbackslash 预测} & \multicolumn{2}{c|}{预测类别} & \multirow{2}{*}{行总计} \\ \cline{2-3}
		& 正常 (0) & 异常 (1) & \\ \hline
		真实正常 (0) & 374 (TN) & 13 (FP) & 387 \\ \hline
		真实异常 (1) & 57 (FN) & 34 (TP) & 91 \\ \hline
		列总计 & 431 & 47 & 478 \\ \hline
		\end{tabular}
	\end{table}

	\begin{table}[H]
	\centering
	\caption{模型性能指标}
	\label{tab:performance_metrics}
		\begin{tabular}{|l|c|}
		\hline
		\multicolumn{1}{|c|}{指标} & 值 \\ \hline
		总体准确率 & 88.0\% \\ \hline
		敏感性（召回率） & 50.0\% \\ \hline
		特异性 & 95.2\% \\ \hline
		精确率 & 66.7\% \\ \hline
		F1-Score & 57.2\% \\ \hline
		\end{tabular}
	\end{table}