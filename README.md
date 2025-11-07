<html lang="en">
<head>
<meta charset="utf-8" />
<meta name="viewport" content="width=device-width, initial-scale=1" />
<title>Project Proposal: Application of Machine Learning in Heart Attack Risk Analysis</title>
<link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;600;700&display=swap" rel="stylesheet">
<style>
  :root{
    --brand:#1f4ed6;
    --ink:#111827;
    --muted:#6b7280;
    --paper:#ffffff;
    --bg:#f5f7fb;
    --card:#ffffff;
    --shadow:0 6px 18px rgba(17,24,39,.08);
  }
  html,body{height:100%;}
  body{
    margin:0; background:var(--bg); color:var(--ink);
    font-family:Inter,system-ui,-apple-system,Segoe UI,Roboto,Ubuntu,"Helvetica Neue",Arial;
    line-height:1.6; font-size:16px;
  }
  .wrap{max-width:980px;margin:32px auto;padding:0 18px;}
  header{
    background:var(--paper); border-radius:14px; box-shadow:var(--shadow);
    padding:28px 28px 20px; margin-bottom:18px;
  }
  header h1{margin:0 0 6px; font-size:28px; font-weight:700; letter-spacing:.2px;}
  header .meta{color:var(--muted); font-size:14px;}
  .card{
    background:var(--card); border-radius:14px; box-shadow:var(--shadow);
    padding:26px 28px; margin:14px 0;
  }
  .content{counter-reset: section;}
  .section{counter-increment: section; counter-reset: subsection;}
  .section > h2::before{
    content: counter(section) ". ";
    color:var(--brand);
  }
  .section > h2{
    margin:0 0 14px; font-size:22px; letter-spacing:.2px;
    border-left:4px solid var(--brand); padding-left:10px;
  }
  .subsection{margin-top:14px; counter-increment: subsection;}
  .subsection > h3::before{
    content: counter(section) "." counter(subsection) " ";
    color:var(--brand);
  }
  .subsection > h3{
    margin:12px 0 6px; font-size:18px;
  }
  p{margin:8px 0;}
  a{color:var(--brand); text-decoration:none;}
  a:hover{text-decoration:underline;}
  ul{margin:6px 0 10px 18px;}
  .ref{color:var(--muted); font-size:14px;}
  .footer{color:var(--muted); text-align:center; font-size:13px; margin:22px 0 10px;}
  @media print{
    body{background:#fff;}
    header,.card{box-shadow:none;border:1px solid #e5e7eb;}
  }
</style>
</head>
<body>
  <div class="wrap">
    <header>
      <h1>Project Midterm: Application of Machine Learning in Heart Attack Risk Analysis</h1>
      <div class="meta">Group 14 · November 2025</div>
    </header>

    <main class="content">
      <!-- 1. Introduction -->
      <section class="card section">
        <h2>Introduction</h2>

        <div class="subsection">
          <h3>Literature Review</h3>
          
          <p> Early research on cardiovascular risk prediction relied on population studies. The Framingham Risk Score showed that blood pressure and cholesterol categories could predict coronary heart disease. Later, the Reynolds Risk Score introduced new biomarkers. It included high-sensitivity C-reactive protein and family history. This addition improved risk classification for women.These scoring systems remain important in clinical practice. However, they rely on fixed categories and linear models. They cannot capture the complex and nonlinear interactions between many risk factors. Consequently, there is an urgent need for more accurate and interpretable prediction models.</p>

          <p><strong>Supervised machine learning.</strong> extends beyond traditional regression approaches. These methods learn directly from labeled data. Support Vector Machines (SVMs) create strong classification boundaries in high-dimensional spaces. Ensemble methods, such as Random Forests and Gradient Boosting models (XGBoost, LightGBM, CatBoost), often outperform single classifiers on heart-disease datasets. These models capture nonlinear patterns and interactions between features. Neural networks, especially Convolutional Neural Networks (CNNs), were first developed for image recognition. They are now adapted to analyze ECG signals and other physiological data for cardiac prediction. </p>

          <p><strong>Unsupervised methods.</strong> also assist researchers in identifying hidden patterns without using outcome labels. K-means clustering divides patient groups into subgroups that share similar characteristics. These clusters can reveal distinct cardiovascular phenotypes. Hierarchical clustering produces tree-like structures of subgroups. This approach is often highly interpretable in clinical practice. Dimensionality reduction methods, such as PCA and t-SNE, are also applied to cardiovascular data. They enable the visualization of risk profiles and uncover structure in high-dimensional features. These methods support exploratory risk stratification and provide insights that can guide feature engineering for supervised models.</p>
        </div>

        <div class="subsection">
          <h3>Dataset Description</h3>
          
          <p>The dataset is taken from Kaggle’s <a href="https://www.kaggle.com/datasets/iamsouravbanerjee/heart-attack-prediction-dataset" target="_blank">Heart Attack Prediction Dataset</a>. It includes patient demographics, medical history, lifestyle factors, and socioeconomic indicators. The target variable is Heart Attack Risk, labeled as high or low risk.</p>
        </div>
      </section>

      <!-- 2. Problem Definition -->
      <section class="card section">
      
        <h2>Problem Definition</h2>

        <div class="subsection">
          <h3>Problem</h3>
          <p>Heart attacks remain one of the leading causes of morbidity and mortality worldwide, accounting for millions of deaths each year. Despite advances in clinical diagnosis, many patients still lack timely risk assessment before symptoms appear, resulting in missed opportunities for early intervention. Traditional approaches, such as the Framingham Risk Score, rely heavily on limited clinical indicators (e.g., blood pressure, cholesterol) and physician expertise.  However, these factors are insufficient to capture the complex interactions among medical, lifestyle, and socioeconomic factors.</p>
        </div>

        <div class="subsection">
          <h3>Motivation</h3>
          <p>To effectively reduce the incidence and mortality of heart attacks, it is urgent to establish a data-driven prediction method that can integrate medical indicators, lifestyle factors, and socioeconomic environments to classify and predict patients’ risk of heart attacks. Machine learning provides an effective solution, as it can capture complex and nonlinear relationships among heterogeneous features. Such predictive models can support early diagnosis, enable personalized interventions, and ultimately assist healthcare providers in making informed clinical decisions.</p>
        </div>
      </section>


      <section class="card section">
        <h2>Methods</h2>
        <div class="subsection">
          <h3>Data Preprocessing</h3>
          <p>
          <strong>Data preprocessing</strong> was automated to ensure data consistency and improve model performance. The pipeline included <strong>blood pressure feature splitting</strong>, categorical <strong>encoding</strong>, and <strong>log transformations</strong> for skewed variables. A <strong>multi-scale feature scaling</strong> strategy was applied, comparing the performance of <em>StandardScaler</em>, <em>RobustScaler</em>, and <em>MinMaxScaler</em> to enhance model stability and convergence across different algorithms.
        </p>
        </div>
        <div class="subsection">
          <h3>Heart Attack Risk Triage</h3>
<p>
  <strong>Unsupervised learning methods</strong> were implemented to perform heart attack risk triage 
  and uncover hidden structure within the dataset. The main objective was to identify subgroups of patients 
  who share similar medical and lifestyle characteristics, providing a data-driven view of heart attack risk stratification.
</p>

<p>
  Three clustering algorithms were applied to achieve robust and diverse grouping outcomes: 
  <strong>K-Means</strong>, <strong>Gaussian Mixture Model (GMM)</strong>, and 
  <strong>DBSCAN (Density-Based Spatial Clustering of Applications with Noise)</strong>. 
  These methods were selected to capture different types of data distributions — 
  K-Means for compact spherical clusters, GMM for probabilistic soft clustering, 
  and DBSCAN for discovering irregular shapes and outliers.
</p>
        </div>
        <div class="subsection">
          <h3>Heart Attack Risk Classification</h3>
          <p>
  <strong>Supervised learning methods</strong> were employed for heart attack risk classification. 
  Two nonlinear ensemble models, <strong>Random Forest</strong> and <strong>XGBoost</strong>, 
  were implemented to perform binary prediction of high- and low-risk patients.
</p>

<p>
  Both models were chosen for their ability to capture complex nonlinear interactions 
  between medical, demographic, and lifestyle features, which are often missed by traditional linear classifiers. 
  Extensive feature engineering and scaling were conducted prior to model training to ensure consistency across predictors.
</p>

<p>
  To address class imbalance in the dataset, the 
  <strong>SMOTE</strong> (Synthetic Minority Oversampling Technique) algorithm was applied, 
  generating synthetic samples for underrepresented classes and ensuring balanced representation 
  between minority and majority groups. 
  This approach enhanced model generalization and reduced bias toward the dominant class.
</p>

        </div>
      </section>
      <section class="card section">
      <h2>Results and Discussion</h2>
      <div class="subsection">
      <h3>Metrics</h3>
      
      <p>
  To identify the most stable cluster configuration, an 
  <strong>optimal cluster analysis</strong> was performed using automated 
  <em>k</em>-value optimization across multiple internal validation metrics. 
  The <strong>Elbow method</strong> and the <strong>Silhouette Score</strong> curve helped determine the appropriate 
  number of clusters for K-Means by balancing compactness and separation.
</p>

<figure style="text-align:center;">
  <img src="figures/optimal_k_analysis_KMeans.png" alt="Optimal K analysis" width="85%">
  <figcaption><strong>Figure 1.</strong> Determining the optimal number of clusters for K-Means using inertia, 
  Silhouette, Davies–Bouldin, and Calinski–Harabasz metrics.</figcaption>
</figure>

<p>
  After selecting the optimal <em>k</em>, a comprehensive comparison was made across 
  <strong>K-Means</strong>, <strong>GMM</strong>, and <strong>DBSCAN</strong> algorithms.  
  Evaluation metrics such as the <em>Silhouette Score</em>, <em>Davies–Bouldin Index</em>, and 
  <em>Calinski–Harabasz Score</em> were used to assess clustering quality from multiple perspectives.  
  This analysis demonstrated that K-Means achieved the best balance between cohesion and separation, 
  providing interpretable and consistent subgroup structures.
</p>

<figure style="text-align:center;">
  <img src="figures/clustering_evaluation_comparison.png" alt="Clustering algorithm comparison" width="85%">
  <figcaption><strong>Figure 2.</strong> Comparison of clustering performance across K-Means, GMM, and DBSCAN 
  using Silhouette, Davies–Bouldin, and Calinski–Harabasz metrics.</figcaption>
</figure>

     <h3>Supervised Model Evaluation</h3>
<p>
  To evaluate model robustness, hyperparameter tuning experiments were conducted for both Random Forest and XGBoost classifiers. 
  Validation accuracy was tracked across different parameter configurations to identify optimal depth and estimator settings.
</p>

<figure style="text-align:center;">
  <img src="figures/tuning_trends_RF.png" alt="Random Forest tuning trends" width="75%">
  <figcaption><strong>Figure 1.</strong> Validation accuracy of Random Forest across different numbers of estimators and maximum tree depths.</figcaption>
</figure>

<figure style="text-align:center;">
  <img src="figures/tuning_trends_XGB.png" alt="XGBoost parameter combinations" width="85%">
  <figcaption><strong>Figure 2.</strong> Top XGBoost parameter combinations ranked by accuracy and F1-score during hyperparameter optimization.</figcaption>
</figure>
      </div>
      </section>
      <p class="footer">© 2025 Group 14 · This page is a static site built for course presentation.</p>
    </main>
  </div>
</body>
</html>
