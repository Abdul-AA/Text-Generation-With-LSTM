# Text Generation using LSTM

## Objective
This project explores the capabilities of Recurrent Neural Networks (RNNs), specifically Long Short-Term Memory (LSTM) networks, in generating text sequences. The goal is to train an LSTM on Shakespeare's writings to generate text in a similar style.

## Dataset
The dataset used consists of the complete works of Shakespeare, a rich and complex corpus widely used for text generation tasks.

## Methodology

### Data Preprocessing
The text data was preprocessed by:
- Converting all characters to lowercase.
- Removing punctuation.

This standardization reduced the complexity of the vocabulary. The processed text was then tokenized into sequences suitable for training an LSTM.

### Model Architecture
An LSTM network was chosen due to its ability to capture long-term dependencies in sequence data. The architecture includes:
- **Embedding Layer**: Converts input characters into dense vectors.
- **LSTM Layers**: Two LSTM layers with 512 hidden units each.
- **Dropout Layer**: Adds regularization to prevent overfitting.
- **Fully Connected Layer**: Projects LSTM outputs to the character set size.

#### Model Architecture Diagram
\begin{figure}[h]
    \centering
    \begin{tikzpicture}
        % Input layer
        \node at (0, 0) [circle, draw, minimum size=1cm] (input) {Input};
        
        % Embedding layer
        \node at (3, 0) [rectangle, draw, minimum width=3cm, minimum height=1cm] (embed) {Embedding Layer};
        
        % LSTM layers
        \node at (7, 1.5) [rectangle, draw, minimum width=3cm, minimum height=1cm] (lstm1) {LSTM Layer 1};
        \node at (7, -1.5) [rectangle, draw, minimum width=3cm, minimum height=1cm] (lstm2) {LSTM Layer 2};
        
        % Dropout layer
        \node at (11, 0) [rectangle, draw, minimum width=3cm, minimum height=1cm] (dropout) {Dropout Layer};
        
        % Fully connected layer
        \node at (15, 0) [rectangle, draw, minimum width=3cm, minimum height=1cm] (fc) {Fully Connected Layer};
        
        % Output layer
        \node at (18, 0) [circle, draw, minimum size=1cm] (output) {Output};
        
        % Connections
        \draw[->] (input) -- (embed);
        \draw[->] (embed) -- (lstm1);
        \draw[->] (embed) -- (lstm2);
        \draw[->] (lstm1) -- (dropout);
        \draw[->] (lstm2) -- (dropout);
        \draw[->] (dropout) -- (fc);
        \draw[->] (fc) -- (output);
    \end{tikzpicture}
    \caption{Detailed LSTM Model Architecture}
    \label{fig:architecture}
\end{figure}

### Training
The model was trained using the Adam optimizer. Early stopping was implemented to prevent overfitting, and model checkpoints were used to save the best-performing model based on validation loss. The final validation loss achieved was 0.253, after which the early stopping criterion was triggered, indicating no improvement in the last 10 epochs.

### Text Generation Primer
To generate text, the trained model starts with an initial seed string. It predicts the next character in the sequence, appends it to the input, and uses this new string to predict the subsequent character. This iterative process produces a sequence of text.

## Results and Discussion
The generated text exhibited coherent structure and stylistic similarities to Shakespeare's original works. The LSTM model effectively captured long-range dependencies, making it suitable for this task. However, the training process was computationally intensive and time-consuming. The resulting text was somewhat coherent and could be improved by training over more epochs.

## Future Work
To improve the model, the following steps can be taken:
- Experiment with different neural network architectures such as GRU or deeper LSTMs.
- Utilize more advanced regularization techniques to prevent overfitting.
- Implement transfer learning using pre-trained language models.
- Optimize the code for better performance to reduce computational expense.

## Conclusion
This project successfully demonstrated the use of LSTM networks for text generation, producing text that mimics the style of Shakespeare. Future improvements could enhance the coherence and quality of the generated text.
