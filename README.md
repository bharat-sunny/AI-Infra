
# Transformer-Based Chat Application

This project leverages the Hugging Face `transformers` library to deploy a BERT model for a chat-based application in a Kubernetes environment. The application uses a pre-trained `bert-base-uncased` model to perform fill-mask tasks, making it suitable for applications involving natural language processing tasks like chat, text completion and text-based predictions.

## Project Setup

The Docker container is based on the Hugging Face `transformers-pytorch-cpu` image and includes essential packages such as `FastAPI` and `Uvicorn` for API management.

### Dockerfile Highlights

- **Base Image**: `huggingface/transformers-pytorch-cpu`
- **Model & Tokenizer**: BERT `bert-base-uncased` is preloaded.
- **Packages**: PyTorch, NumPy, FastAPI, Uvicorn, and Hugging Face transformers are installed using both pip and mamba (a faster conda alternative).
- **Entry Point**: The application serves a fill-mask task on port `8888` using the `transformers-cli`.

### Docker Commands

To build and run the Docker container locally, use the following commands:

1. **Build the Docker Image:**

   ```bash
   docker build -t bert-chat-app .
   ```

2. **Run the Docker Container:**

   ```bash
   docker run -p 8888:8888 bert-chat-app
   ```

## Kubernetes Deployment

To deploy this application in Kubernetes, follow these steps:

## Deploy to Kubernetes:

   ```bash
   kubectl apply -f deployment.yaml
   kubectl apply -f service.yaml
   ```

## Using the Application

Once deployed, the application will be accessible through the service’s external IP. It runs a fill-mask task on `bert-base-uncased`, making it suitable for tasks such as auto-completion and NLP-based chat functionalities.

## Additional Notes

- **Port**: Ensure that the port `8888` is accessible in your Kubernetes cluster.
- **Scaling**: Adjust the number of replicas as needed in the `deployment.yaml` to scale the application horizontally.

## Dependencies

- [Hugging Face Transformers](https://huggingface.co/transformers/)
- [FastAPI](https://fastapi.tiangolo.com/)
- [Uvicorn](https://www.uvicorn.org/)
- PyTorch (CPU)