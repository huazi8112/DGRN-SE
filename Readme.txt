1.System requirements
-------------------------
a. We implemented the codes with MATLAB R2024a on Windows11.

2.Document description:
-------------------------
program：
        plot:
	bar_plot.m : Main script for drawing clustered grouped histograms
	bar_figure.m : Function to draw clustered grouped histograms
	bar_figure.m : Function to draw clustered grouped histograms
	psortBar.m：The main script to draw a histogram of the average p value of each gene combination
	FilledPlot3.m：Function to draw a three-dimensional filled line chart
	t_FilledPlot3.m：Script to draw three-dimensional filled line chart of gene expression (TPM) of each sensitive gene
	SankeyChart.m：Functions that draw Sankey diagrams
	SankeyPlot.m：Script to draw a Sankey diagram of the relationship between sensitive genes and diseases
	data-(dataset).xlsx：A table that stores the data required for a Sankey diagram

	The main difference between Dataset hESC program and Dataset mESC and Dataset GM  program lies in the different input data sets. The following sub-file description applies to the aforementioned three dataset:
	-------------------------
	Data preprocessing:
		preprocess.m ：The main script for data preprocessing
		p_data.mat ：A data preprocessing function that includes the average processing of 0 values and the moving average processing of the original data
                calcRb:Calculates RB values
                detectStableInterval:Detects stable time intervals in gene expression data
                praWAVE:Processes time-series data using wavelet transforms
		t_wavelet-hESC：Post-processing data obtained after data preprocessing
		500_ChIP-seq_(dataset)-ExpressionData.xlsx：Files for processing and analyzing Dataset 
                500_ChIP-seq_(dataset)-network.xlsx:Validated gene-gene interaction network

	kmeans++:
		kmeans_plusplus1.m：kmeans++ algorithm script 
		transition.m ：The gene expression time series is transformed into a function of gene dynamics (gene expression distribution)
		setHandel.m ：A function to set the drawing window size
		outpng.m ：A function that outputs a picture
                kmeans_wavelet-(dataset):K-means++ clustering results on wavelet-processed data

	Build a gene network:
                GCNtest.py: Implements a graph autoencoder to reconstruct gene interaction networks from preprocessed data and validated edges.
		getpre.m: Generates  prewavelet-kx-(dataset).mat
		prewavelet-kx-(dataset).mat ：The corresponding results of constructing gene network scripts for Class x of [dataset]

	Identify sensitive genes and gene combinations：
	Initial network entropy index calculation:
		c_index0.m：A script to calculate the initial network entropy
		refine_Main_ARNN.m：ARNN function
		NN_F2.m：The function that is required to process the data in the ARNN algorithm prediction process
		Stem3D.m：A function for drawing 3D stem diagrams
		error.mat：ARNN prediction error saved after running
		init_indext_wavelet-kx-(dataset).mat：The initial overall network entropy of the output for Class x of [dataset]

	Disturbance handling:
		raodong_point.m ：A script that perturbs each gene to different degrees and determines whether there is a significant impact on the system after perturbation
		Butterfly.m ：A function for drawing butterflies
		StackedButterflyPlot.m ：A function that draws a stacked butterfly diagram
		adduwaveletkx-500-(all)-(dataset) ：The result of output from script raodong point.m after perturbation processing  for Class x of [dataset]

	Subnetwork exploration:
		final_test.m ：Generate subgraph vertex combination to do the perturbation processing and identify its influence and function script
		net_train.m ：Calculate the function of generating the initial network entropy index of the subgraph
		final_result1_wavelet-kx(t)-(dataset).mat：The result of the final test.m script for Class x of [dataset]

	Draw gene subnetworks:
		Gplot.m：Script to draw gene subnetworks

Figures and Tables:
       The  two  document compiles all figures and tables generated in the study.
3.Use script sequence：
-------------------------
preprocess.m-->kmeans_plusplus-(dataset).m-->GCNtest.py-->getpre.m -->c_index0.m-->raodong_point.m-->final_test.m 
Note:  The .mat files in different folders are needed to updat during operation.
	
